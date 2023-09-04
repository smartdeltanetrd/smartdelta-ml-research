# DS Analysis for SmartDelta

## Python Intercative Environment

1. First time after cloning new environment should be created (from the **repo root directory**):
    ```
    python3 -m venv .venv
    ```
1. Activate the environment:
    ```
    source .venv/bin/activate
    ```

## Jupyter Notebook Server

Run the following **from the project directory** to start the server:
```
docker run --runtime=nvidia -d --rm -v ~:/home/${USER} --net=host --name="${USER}_smartdelta_jupyter_server" ${USER}_smartdelta_ds bash -c "cd $(pwd) && if [ ! -d ".venv" ]; then python3 -m venv .venv && source .venv/bin/activate && pip3 install notebook; else source .venv/bin/activate; fi && PYTONPATH=$(pwd) jupyter notebook --collaborative --port 8888 --ip 0.0.0.0 --NotebookApp.token=1603e1fd7ad2f198c02d4a9774332c77520fdd130482a773"
```


