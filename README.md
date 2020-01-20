# Packer for GCP

## Documentation 
* [basic usage](https://www.packer.io/intro/getting-started/build-image.html)
* [Google Compute Builder](https://www.packer.io/docs/builders/googlecompute.html)

## Executing Packer from a non GCE instance 

First download the json key of a existing Service Account with granted roles of:

* Compute Admin 
* Service Account User

Packer looks for credentials in the following places, preferring the first location found:

1. An `account_file` option in your packer file.

2. A JSON file (Service Account) whose path is specified by the GOOGLE_APPLICATION_CREDENTIALS environment variable.

3. A JSON file in a location known to the gcloud command-line tool. (gcloud auth application-default login creates it)


## How to build an image

### Edit custom-images.json file
Add the right data according to your Google Cloud Platform porject settings

* `project_id`
* `network`
* `network_project_id`
* `subnetwork`

Review if you need it to be `preemtible`, or `omit_external_ip` and change decriptions and names accordingly


### Test the json packer manifest
```
packer validate <file-name>.json
```

### Build the image
```
packer build <file-name>.json
```

### Review created image 
Check the image from **Custom images** menu in **New VM instance** Compute Engine menu
