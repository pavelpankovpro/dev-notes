# To install virtualenv via pip
pip3 install virtualenv

# Note that virtualenv installs to the python3 directory. For me it's:
/usr/local/share/python3/virtualenv

# Create a virtualenvs directory to store all virtual environments
mkdir somewhere/virtualenvs

# Make a new virtual environment with no packages
virtualenv somewhere/virtualenvs/<project-name> --no-site-packages

# To use the virtual environment
cd somewhere/virtualenvs/<project-name>/bin
source activate

# You are now using the virtual environment for <project-name>. To stop:
deactivate

# export requirements
pip freeze > requirements.txt

# import requirements
pip install -r requirements.txt

# refresh virtualenv
virtualenv --clear env
