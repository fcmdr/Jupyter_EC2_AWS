# Jupyter_EC2_AWS
Goal : Working with Jupyter into an EC2 Instance in AWS from a browser page


## Connect to ec2-instance 
Shortcut to ssh if not working directly in Windows 10 : ```cd "C:\Windows\System32\OpenSSH"``` we can also modify environment variables to be able to launch ssh from any path. We place ourself into the directory containing the key and the script 
```cd "C:\Users\Fouad\Desktop\DSTI courses\AWS"```

### Send python script to the ec2 instance via ssh
Connection to the ec2-instance via ssh```ssh -i "Fouad_A19_KeyPair.pem" ubuntu@ec2-184-73-85-174.compute-1.amazonaws.com```
Send the file from the local computer to the ec2-instance ```scp -i "C:\Users\Fouad\Desktop\DSTI courses\AWS\Fouad_A19_KeyPair.pem" "C:\Users\Fouad\Desktop\DSTI courses\AWS\ec2_python_script.py" ubuntu@184.73.85.174:/home/ubuntu/ec2_python_script.py```
### To launch script from python
python3 ec2_python_script.py

### Upgrade and install python 3.6
sudo apt-get upgrade
sudo apt-get install python3.6

## Install jupyter and pip3
sudo apt install python3-pip
pip install jupyter

## Launch Jupyter Notebook 
jupyter notebook --ip=0.0.0.0 --no-browser
Type on a browser page the "IP_address_of_the_ec2-instance:Jupyter port(8888)" example :``http://184.73.85.174:8888``

To keep jupyter server sessions "alive" we can launch a cmd in a parallel cmd line and works with it (the following command works for any cmd line)
``nohup jupyter notebook --ip=0.0.0.0 &``
Jupyter will run even after shutting down we can display the characteristic of the jupyter notebook session so we get our token
```cat nohup.out```
```kill "id_nb_jup_browser"```


## Create environments through Anaconda or pew

-Create a new folder :
```mkdir /tmp```
```cd /tmp```

### Option 1 : Launch environments with "Anaconda" : 
```curl -O https://repo.anaconda.com/archive/Anaconda3-2019.03-Linux-x86_64.sh```
```bash Anaconda3-2019.03-Linux-x86_64.sh```

### Option 2 : Launch environments with "Pew" :
-Install pew
```pip3 install pew```
-Create a new environment with pew
```pew new test_env```
```pew ls```` to see all environments availables
```pew workon test_env```
-It is necessary to install kernel when using several environments with the package ipykernel 
```sudo pip3 install ipykernel```
```python3 -m ipykernel install --user --name=Python_env```

Save all dependencies into a text file "requirements.txt" ```pip3 freeze > requirements.txt```

### Launch jupyter:
```jupyter notebook --ip=0.0.0.0 --no-browser```

-Install a package in our new environment pandas by example
```sudo apt-get install python3-pandas```
```import pandas as pd```

## To list the availables kernel environments
 ```jupyter kernelspec list```
 ** When deleting environments to avoid kernel errors use this command ** ```jupyter kernelspec uninstall env```
 
## Result 

<img width="911" alt="Env_image" src="https://user-images.githubusercontent.com/58029143/70162344-c9e3c900-16bd-11ea-9fda-048eb1f9793c.png">


