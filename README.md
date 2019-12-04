# Jupyter_EC2_AWS
Goal : Working with Jupyter into an EC2 Instance in AWS from a browser page


## Connect to ec2-instance 
Shortcut to ssh if not working directly in Windows 10 : ```cd "C:\Windows\System32\OpenSSH"``` we cal also modify environment variables to be able to launch ssh from any path  

### Go into the directory
``cd "C:\Users\Fouad\Desktop\DSTI courses\AWS"``
### Send python script to the ec2 instance 
ssh -i "Fouad_A19_KeyPair.pem" ubuntu@ec2-184-73-85-174.compute-1.amazonaws.com
#send on ec2 machine
scp -i "C:\Users\Fouad\Desktop\DSTI courses\AWS\Fouad_A19_KeyPair.pem" "C:\Users\Fouad\Desktop\DSTI courses\AWS\ec2_python_script.py" ubuntu@184.73.85.174:/home/ubuntu/ec2_python_script.py
### To launch script from python
python3 ec2_python_script.py

### Upgrade and install python 3.6
sudo apt-get upgrade
sudo apt-get install python3.6

# Install jupyter and pip3
sudo apt install python3-pip
pip install jupyter

jupyter notebook --ip=0.0.0.0 --no-browser
http://184.73.85.174:8888
#keep jupyter server sessions alive
#launch a cmd in a parallel cmd line and works for any cmd line
nohup jupyter notebook --ip=0.0.0.0 &
#Jupyter will run even after shutting down 
#display what jupyter displays so we have our token
```cat nohup.out```
```kill id_nb_jup_browser```


## Create environments though Anaconda or pew

-Create a new folder :
```mkdir /tmp```
```cd /tmp```
```curl -O https://repo.anaconda.com/archive/Anaconda3-2019.03-Linux-x86_64.sh```
```bash Anaconda3-2019.03-Linux-x86_64.sh```
## Launch environments with Pew
-Install pew
```pip3 install pew```
-Create a new environment with pew
```pew new test_env```
```pew ls```` to see all environments availables
```pew workon test_env```
```python3 -m ipykernel install --user --name=nameyouwantinjupyter```

```pip3 freeze```



#pew
pip install pew
pew new Fouad_env
pew ls

#
```sudo pip3 install ipykernel```
```python3 -m ipykernel install --user --name=nameyouwantinjupyter```

#Launch jupyter:
```jupyter notebook --ip=0.0.0.0 --no-browser```

-Install a package in our new environment
```sudo apt-get install python3-pandas```
```import pandas as pd```

## To list the availables kernel environments
 do ```jupyter kernelspec list```
 ```jupyter kernelspec uninstall env```
 
## Result 

<img width="911" alt="Env_image" src="https://user-images.githubusercontent.com/58029143/70162344-c9e3c900-16bd-11ea-9fda-048eb1f9793c.png">


