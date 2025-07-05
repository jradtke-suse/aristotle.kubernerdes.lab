# README

Status: Work In Progress.  At this point I am just keeping notes here.
Purpose: documenting some "pro-tips" for deploying SUSE training on a local machine.

I chose to call my training host Aristotle after the Greek Trainer.

## Steps
Download all the course material from the S3 bucket (you will need access)
ProTip:  using the AWS CLI is much better (but.. beyond the scope of this explanation at this point)

Install the base image on to your training host (I opted for openSUSE_Leap-15.3-desktop-9.0.2.iso) - you will find the S3 URI in the "Lab Machine and Course VM Download Links" doc in the course you are taking.

```
geeko:Training jradtke$ ls Training_Base_Image/
openSUSE_Leap-15.2-desktop-8.0.3.iso		openSUSE_Leap-15.3-desktop-9.0.2.iso.md5sum	README-Live_Image_Options.pdf
openSUSE_Leap-15.2-desktop-8.0.3.iso.md5sum	openSUSE_Leap-15.3-desktop-9.0.2.qcow2
openSUSE_Leap-15.3-desktop-9.0.2.iso		openSUSE_Leap-15.3-desktop-9.0.2.qcow2.md5sum
```

copy all the training files to `/install/courses/<course name/number>
```
tux@aristotle:/install/courses> find /install/courses -maxdepth 1
/install/courses
/install/courses/SLE201v15
/install/courses/KUB211v1.24
/install/courses/install_a_lab_environment.mp4
```

```
/install/courses/SLE201v15/Images
/install/courses/SLE201v15/Manuals
```

NOTE:  7z is particularly sensitve to options and spacing (notice there is no space between the '-o' and 'extracted/'
```
cd /install/courses/SLE201v15/Images
7z x sle201v15.5-10-21-2024.7z.001  -oextracted/
```

```
cd extracted/sle201v15.5-installer
tux@aristotle:/install/courses/SLE201v15/Images/extracted/sle201v15.5-installer> ls -la
total 104
drwxr-xr-x 5 tux users  4096 Jul 12  2024 .
drwxr-xr-x 3 tux users  4096 Jun 23 14:36 ..
-rwxr-xr-x 1 tux users 17318 Nov  8  2023 backup_lab_env.sh
-rwxr-xr-x 1 tux users  1674 Nov  8  2023 changelog
drwxr-xr-x 4 tux users  4096 Jul 15  2024 config
-rwxr-xr-x 1 tux users  4461 Nov  8  2023 install_lab_env.sh
-rwxr-xr-x 1 tux users  1066 Nov  8  2023 LICENSE
-rwxr-xr-x 1 tux users  9890 Nov  8  2023 README-lab_environment_standards.md
-rwxr-xr-x 1 tux users 32457 Nov  8  2023 README.md
-rwxr-xr-x 1 tux users  3328 Nov  8  2023 remove_lab_env.sh
drwxr-xr-x 2 tux users  4096 Nov  8  2023 scripts
drwxr-xr-x 2 tux users  4096 Oct  3  2024 VMs
```


Login info: tux / linux

You will need saml2aws and "myaccount.suse.com" auth token
```
saml2aws login
aws --profile testtraining s3 ls
aws --profile testtraining s3 ls s3://s3-suse-ec1-tm-training/VM\ Files/Rancher/
# Ugh.. there is a random folder in the bucket (at least I presume it's random)
#aws --profile testtraining s3 sync  s3://s3-suse-ec1-tm-training/VM\ Files/Rancher/KUB211v1.24/  ./KUB211v1.24/
aws --profile testtraining s3 sync  s3://s3-suse-ec1-tm-training/VM\ Files/Rancher/KUB211v1.24/  ./KUB211v1.24/ --exclude "Files for Namrata"
```
