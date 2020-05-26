# Machines

1) Kaggle 30h GPU
2) stugpu2
2-1) uploading data: CyberDuck
2-2) jupyter: 

on server
```
ssh -X u6849956@partch.anu.edu.au
ssh -X stugpu2
anaconda3
jupyter notebook --no-browser --port=7000
```
on local machine
```
ssh -A -t -l u6849956 partch.anu.edu.au -L 7000:localhost:7000 ssh -A -t -l u6849956 stugpu2.anu.edu.au -L 7000:localhost:7000
```

2-3) server jupyter config
```
~/.local/bin/jupyter-noteboo --generate-config
vi ~/.jupyter/jupyter_notebook_config.py

c.NotebookApp.allow_origin = '*' #allow all orig
c.NotebookApp.ip = '0.0.0.0' # listen on all IPs
c.NotebookApp.port = 7000
c.NotebookApp.password = ''
c.NotebookApp.token = ''
c.NotebookApp.allow_remote_access = True
```
