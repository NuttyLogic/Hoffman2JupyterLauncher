# Hoffman2JupyterLauncher
[Hoffman2JupyterLauncher.py](https://github.com/NuttyLogic/Hoffman2JupyterLauncher) automates launching a remote jupyter notebook instance on the UCLA Hoffman2 cluster and forwarding the jupyter notebook port to your local machine. 
This script is a refactored version a [script](https://gitlab.idre.ucla.edu/dauria/jupyter-notebook) 
provided by the UCLA [IDRE](https://idre.ucla.edu/). This script will fail if the port forwarded is in use. 

```bash
usage: python3 Hoffman2JupyterLauncher -u sge_username -t time_in_hours -m memory_in_GB 
                                -s cores -p port -d jupyter_directory
                               -c cluster_address -M module1 -M module2 ...

Script to launch remote jupyter instances on hoffman2

optional arguments:
  -h, --help  show this help message and exit
  -u U        hoffman2 username
  -t T        time in hours, default = 4
  -m M        memory in GB per slot, default = 4
  -s S        slots (cores), default = 2
  -p P        Port to output dictionary, default = 8790
  -d D        hoffman2 directory to initialize jupyter, default = $HOME
  -c C        path to SGE cluster, default = idre.ucla.edu
  -M M        -M for each module you want to load, default python/3.6.1

```

To run the script without specifying inputs, change the default values in the argument parser.

```python
parser.add_argument('-u', type=str, default='sge user', help='hoffman2 username')
parser.add_argument('-t', type=int, default=8, help='time in hours, default = 4 ')
parser.add_argument('-m', type=int, default=8, help='memory in GB per slot, default = 4')
parser.add_argument('-s', type=int, default=2, help='slots (cores), default = 2 ')
parser.add_argument('-p', type=int, default=8790, help='Port to output dictionary, default = 8790, '
                                                       'if port is unavailable script will fail')
parser.add_argument('-d', type=str, default='$HOME', help='hoffman2 directory to initialize jupyter ')
parser.add_argument('-c', type=str, default='hoffman2.idre.ucla.edu', help='path to SGE cluster')
parser.add_argument('-M', type=str, default=['python/3.6.1'], action='append',
                    help='-M for each module you want to load')
```