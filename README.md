# DS Analysis for SmartDelta

## Jupyter Notebook Server

To build container, run the following command from `docker_container_src/xsession-home` directory:
```
docker build --network host -f Dockerfile --build-arg user_name=`id -nu` --build-arg group_name=`id -ng` --build-arg user_uid=`id -u` --build-arg user_gid=`id -g` --tag ${USER}_smartdelta_ds .
```

To start server, run the following **from the project directory**:
```
docker run -d --rm -v ~:/home/${USER} --net=host --name="${USER}_smartdelta_jupyter_server" ${USER}_smartdelta_ds bash -c "cd $(pwd) && if [ ! -d ".venv" ]; then python3 -m venv .venv && source .venv/bin/activate && pip3 install -r requirements.txt; else source .venv/bin/activate; fi && PYTONPATH=$(pwd) jupyter notebook --port 8888 --ip 0.0.0.0 --NotebookApp.token=1603e1fd7ad2f198c02d4a9774332c77520fdd130482a773"
```

