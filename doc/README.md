# Docs with Sphinx

This documentation will be automatically built and generated with continuous integration, via the [circle.yml](../circle.yml). However, if you have need to test locally, you can do that by way of the Dockerfile in this folder. First, build the basic image:

```
cd pydicom/docs
docker build -t pydicom/pydicom-docs .
```

Next, cd back into the repo base. We want to mount from here.

```
cd ..
docker run --volume $PWD:/data -it pydicom/pydicom-docs
```

Then you can build the docs:

```
cd doc && make html
exit
```

You should then be able to cd into `_build/html` on your local machine and preview with your webserver of choice

```
cd doc/_build/html
python -m http.server 9999
```

Then open your browser to [http://127.0.0.1:9999](http://127.0.0.1:9999)
