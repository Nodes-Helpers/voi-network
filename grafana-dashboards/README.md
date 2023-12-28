<h1 align="center">How to monitoring Voi relay node</h1>

**Requirements:**
- Grafana
- Last image of the docker Voi relay node container by [@Urtho](https://github.com/urtho) and [@cswenor](https://github.com/cswenor) from [here](https://github.com/cswenor/voi-relay-setup/blob/main/relay-guide.md)
- Open default Grafana TCP port 3000 for web-interface from source address which you will be use

**This guide mean what you has installed Voi relay node by docker**

### Install Grafana ###
We will install Grafana on Ubuntu system. You can install Grafana on your server with Voi node or your another server.

1. Install the prerequisite packages:
   
   ```
   sudo apt-get install -y apt-transport-https software-properties-common wget
   ```
2. Import the GPG key:

   ```
   sudo mkdir -p /etc/apt/keyrings/
   wget -q -O - https://apt.grafana.com/gpg.key | gpg --dearmor | sudo tee /etc/apt/keyrings/grafana.gpg > /dev/null
   ```
3. To add a repository for stable releases, run the following command:

   ```
   echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
   ```

4. Run the following command to update the list of available packages:

   ```
   sudo apt-get update -y
   ```

5. To install Grafana OSS, run the following command:

   ```
   sudo apt-get install grafana -y
   ```
6. For check correct installation you can use:

   ```
   systemctl status grafana-server
   ```
   You should see ```Active: active (running)``` state.
<br>

Other ways to install Grafana you can find [here](https://grafana.com/docs/grafana/latest/setup-grafana/installation/)

### Configure a Grafana ###

1. Open Grafana web-interface in your browser, address looks like http://[ip of your server]:3000/login
   
   default login is **admin**, password is **admin**

2. Add Prometheus data source

   You should open menu in left upper corner:<br>
   
   ![image](https://github.com/Nodes-Helpers/voi-network/assets/80079858/ae3c3e7c-52b5-48f4-b27c-5a3d1c0aa523)

   Click on Data sources:<br>

   ![image](https://github.com/Nodes-Helpers/voi-network/assets/80079858/e7c5bb63-d193-496d-8059-436dea312d05)

   Click on Add new data source:<br>

   ![image](https://github.com/Nodes-Helpers/voi-network/assets/80079858/6c656558-3ef5-41a5-98d3-c48a046b6c1c)

   Select the Prometheus:<br>

   ![image](https://github.com/Nodes-Helpers/voi-network/assets/80079858/0b93ecdb-930e-4509-81fe-db4b2a584fb2)

   Input address of your Prometheus server:

   ![image](https://github.com/Nodes-Helpers/voi-network/assets/80079858/1540bedd-9071-4cb8-8c25-4636ecbd3fcc)

   - If you installed Grafana on same server with Voi relay node input localhost:9090
   - If you installed Grafana on another server input [ip address of this server]:9090
  
   Click Save & test on the bottom of this page

   ![image](https://github.com/Nodes-Helpers/voi-network/assets/80079858/a3281c2e-6c77-4a09-8b86-7455de275a89)

   You should see next message:

   ![image](https://github.com/Nodes-Helpers/voi-network/assets/80079858/e2548e34-1853-4a42-92ff-5147d2907a92)

### Add a dashboard to Grafana ###

1. Now we should go to Dashboards in left upper corner menu

   ![image](https://github.com/Nodes-Helpers/voi-network/assets/80079858/0d836c6d-5567-4cd2-a697-619b976035d3)

2. Click on the New button and Import button

   ![image](https://github.com/Nodes-Helpers/voi-network/assets/80079858/dff670a3-e2af-467e-b56a-cdf81666cf37)

3. You can download .json file from [here](https://github.com/Nodes-Helpers/voi-network/blob/main/grafana-dashboards/voi-relaynode-dashboard.json) and import this by upload here:

   ![image](https://github.com/Nodes-Helpers/voi-network/assets/80079858/5e1f4289-a01b-4170-9481-2678c2dab4d9)

   Or you can just copy all from [here](https://github.com/Nodes-Helpers/voi-network/blob/main/grafana-dashboards/voi-relaynode-dashboard.json) and paste this to here:

   ![image](https://github.com/Nodes-Helpers/voi-network/assets/80079858/6d9e30f6-940d-46a5-81d3-a8c9ab155a64)

4. Next you should to click the Load button and input name of your Dashboard and click the Import button.
   
6. Dont forget to save dashboard by click this button in right upper corner:

   ![image](https://github.com/Nodes-Helpers/voi-network/assets/80079858/38d7d313-4a60-424c-9b98-9bab5184fa4e)

Enjoy!









