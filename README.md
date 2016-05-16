# Deep Learning

This repository is used to store my progress in Udacity's Deep Learning course.

## 1. Download and run Docker container

`docker run -dit -v /PATH_TO_CONTAINER_DIR:/notebooks -p port:port tensorflow/tensorflow`

Then open the browser and go to [docker_container_ip]:port to verify it is running alright.

Noticed that `port` is a detailed number like "8888" or some other ports you want to use.

Or you can also install Tensorflow in your local machine without in virtual container.

## 2. Update jupyter module

Run bash in docker container:

```bash
docker exec -ti [docker_id] bash
```

Then update the module:

```bash
pip install -U jupyter
```

Then stop jupyter server by running:

```bash
kill $(pgrep jupyter)
```

This will actively stop docker container, Then re-start it again:

```bash
docker start [docker_id]
```

The same procedure can be used to update other modules in python package.

If you are using Jupyter Notebook on localhost but not virtual machine, to update
packages, you just need to running:

```bash
pip install -U package_name
```

## 3. Change the indentation to use 2 spaces

Tensorflow uses 2-space indentation instead of the default 4-space. It is annoying to run the code
on
this default setting so lets change our ipython notebook's config for indentation:
- Open javascript console.
- Run the following code:
```
var cell = Jupyter.notebook.get_selected_cell();
var config = cell.config;
var patch = {
          CodeCell:{
                      cm_config:{indentUnit:2}
                            }
                                }
                                config.update(patch)
                                ```

                                If it returned error `Uncaught TypeError: config.update is not a
                                function(…)` then ipython notebook needs to be updated (see step 2
                                above), then clear browser's cache.
