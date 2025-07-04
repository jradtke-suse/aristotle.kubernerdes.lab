# README

Status: Work In Progress.  At this point I am just keeping notes here.


Download all the course material from the S3 bucket (you will need access)

Install the base image on to your training host

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

