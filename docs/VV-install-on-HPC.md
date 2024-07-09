## Aim
This guide explains how to install Voucher Vision on the high performance compute cluster available to Kew researchers.

## Pre-requisites
- Account on the [crop diversity HPC cluster](https://cropdiversity.ac.uk/), with [key authentication](https://help.cropdiversity.ac.uk/ssh.html) set up.
    - Request an account [here](https://help.cropdiversity.ac.uk/user-accounts.html) if you don't have one already.
- Familiarity with Linux command line to navigate between directories, clone git repositories etc
    - Use the datacamp course [Introduction to the shell](https://www.datacamp.com/courses/introduction-to-shell) if necessary - Kew has [free access to datacamp courses](https://kewnet.kew.org/team_news/free-datacamp-licenses/)

## Setup

You will need to be able to execute commands in three different places, ie:
1. Your *local machine* (assume Windows)
2. The *head node* of the HPC cluster (gruffalo.cropdiversity.ac.uk)
3. A *compute node* on the HPC cluster (assigned on request)

## Installation steps

The instructions below note which machine you should run each on:

1. *(Local machine)* Open a command windows and log into the HPC head node `gruffalo.cropdiversity.ac.uk`
1. *(head node)* [Install bioconda](https://help.cropdiversity.ac.uk/bioconda.html)
1. *(head node)* Request an interactive shell on a node with a GPU: `srsh --partition gpu --gpus=1` Note the name of the compute node that you are assigned - you will need it later
1. *(compute node)* Follow [VoucherVision setup instructions](https://github.com/Gene-Weaver/VoucherVision?tab=readme-ov-file#installing-vouchervision-using-conda)
1. *(compute node)* Run Voucher Vision using the instructions [here](https://github.com/Gene-Weaver/VoucherVision?tab=readme-ov-file#run-vouchervision). Note the port that the web server is listening on.
1. *(local machine)* Set up port forwarding. In a command line shell in your local environment, execute:
   
    `ssh -L8502:GPU_MACHINE_NAME.cropdiversity.ac.uk:8502 YOUR_HPC_USER_NAME@gruffalo.cropdiversity.ac.uk`

   Substitute GPU_MACHINE_NAME and YOUR_HPC_USER_NAME appropriately.
1. *(local machine)* Open the VoucherVision web interface in your local browser at https://127.0.0.1:8502
