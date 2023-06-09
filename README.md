# Distributed Scraping Network

This API is created to run on a server, providing a central means of distributing and collecting 
weather data from [Open-Meteo](https://open-meteo.com/). 
This server provides a means of accessing and running a [DNS leaf](https://github.com/Spatiotemporal-Wildlife-Classification/DSN-Leaf)
node at any computer. This allows collection to occur externally running from a form of cloud computing. 
This allows you to keep your computer free to work on other topics while data collection occurs. 

Please keep in mind that the DSN-leaf should execute a maximum of 10000 requests per day to Open-Meteo. 
Please respect the rate limits, and a thank you to the amazing service they provide. 

The API was created using [FastAPI](https://fastapi.tiangolo.com/)

## How to use
1. Fork this repository and apply the following changes:
    - Replace the interim_sample.csv with an interim csv file generated by the [Spatiotemporal-Wildlife-Classification](https://github.com/trav-d13/spatiotemporal_wildlife_classification) repository
    - This applied to the interim_sample which is a subset of the above file for testing purposes.
    - Replace `interim_felids.csv` in line 87 in `app/main.py` with the name of your file
2. Create a [Linode](https://cloud.linode.com)
    - Create an account with [Linode}(https://cloud.linode.com). They provide a fantastic cloud computing service at reasonable rates. 
    - Access your `Linodes` tab on your account
    - Select `Create Linode` in the top-right corner
    - The Linode should have the following properties:
      - The latest Ubuntu LTS (in this case Ubuntu 22.04 LTS)
      - Select a region close to yourself to speed up communications
      - Linode Plan -> Shared CPU -> Nanode 1GB (5$ per month max)
      - Provide a custom linode label
      - Provide a secure password (keep this around as you will need it shortly)
      - Click `Create Linode`
3. SSH access into the Linode
    - Open a terminal and copy the Linode's SSH key, enter this as a command
    - Enter the password corresponding to the linode
    - You are now in the terminal of the cloud computer service.
    - run `apt-get update` followed by `apt upgrade` to update the system.
    - Run `apt install docker-compose` to install docker
4. Clone a fork of this repository into the terminal using the `git clone` command
5. Rebuild the docker container with the following command: `docker-compose build`
6. Start the server with the following command: `docker-compose up --detach`
   - As the server has been run detached, you can exit the SSH terminal and it will continue running.
7. The resulting endpoint will be as follows: http:// `IP on linode` :5000/
    - Example: http://109.74.200.171:5000/
8. To review the API specifications place `docs` after the URL to access the API swagger to see the API specifications
   - http://109.74.200.171:5000/docs

Many thanks to the original repository at https://github.com/S010MON/distributed-scraping-network from which this repository was developed.
