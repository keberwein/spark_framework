# PySpark Framework

A high-level framework for organizing and submitting PySpark jobs via `spark-submit`.

## Usage

**Run Makefile**
This will create a new folder `dist`, which will house .zip files of our `jobs` module as well as local .zip files of all the dependency packages.

```
make build
```

**Cd into `dist` and run a Spark Submit command.**

```
cd dist && spark-submit --py-files jobs.zip main.py --job wordcount
```


## Structure

* `src`: Holds Python code and copies of requried packages.

    -- `jobs`: Individual PySpark jobs, which can be specified at the command line with `spark-submit`.
    
    -- `libs`: Dependency libraries that are downloaded from pip at or before runtime.
    
    -- `shared`: Code shared by all jobs.
    
    -- `main.py`: The main Python script that defines command line arguments and SparkContext.
    
* `tests`: Unit testing for all jobs

    -- `_jobs`: Directory containing sub-directories for each job and test files.
    
* `requirements.txt`: A list of third-party packages that will be automatically installed from pip into the `src/libs` directory at runtime.

* `dev_requirements.txt`: Dependency packages for the `pyspark` package and others.

* `Makefile`: Installs dependencies and runs tests.
    
