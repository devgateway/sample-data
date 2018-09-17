# Real world OCDS examples

This folder contains real-world examples of OCDS data, plus scripts for fetching data, validating and transforming it.

Each publisher directory contains:

* A ```sample/releases``` folder which contains a small number of example releases, and a ```sample/records``` folder with a small number of example records.
* A ```fetch.py``` script which will get an updated set of examples, or all available releases if you so specify.

## Fetch data

You can fetch data by changing to the target directory, then running:

    python /publisher-name/fetch.py

You will need the current directory in your Python path for this to work. The following command should update the path appropriately.

    PYTHONPATH=$PYTHONPATH:`pwd`

This script defaults to collecting around 10 examples. Add the `--all` argument to fetch all available publications and save them in an `all` folder (which git will ignore).

## Transform data

Once you have downloaded the releases, you can then transform to v1.1 of the OCDS schema, if they are published under a previous schema. Do this with:

    python update_to_v1_1.py -f path/to/releases

Note that this will overwrite the existing files.

## Upload data to BigQuery

You can then upload the transformed records and releases to BigQuery, which lets you run rapid queries using SQL in the cloud. This process is described in `tools/README.md`.
