## Allowing EC2 instances to connect our RDS DB

### Step 1: Create a database, eg:- Mariadb,postgresql etc

![image](https://user-images.githubusercontent.com/54981984/95892095-9c6ab000-0da3-11eb-93bb-6ff60f6d4763.png)

![image](https://user-images.githubusercontent.com/54981984/95892145-af7d8000-0da3-11eb-9861-c835f6674c1a.png)

#### Choose Free tier and give a name for DB instance identifier

![image](https://user-images.githubusercontent.com/54981984/95892302-f79ca280-0da3-11eb-8373-4801baec7620.png)

![image](https://user-images.githubusercontent.com/54981984/95892439-2f0b4f00-0da4-11eb-94d3-3e28cca3a8ae.png)

![image](https://user-images.githubusercontent.com/54981984/95892519-4e09e100-0da4-11eb-8b48-3aa2929c2cb0.png)

![image](https://user-images.githubusercontent.com/54981984/95892573-5cf09380-0da4-11eb-8e7d-cb6a1cb81259.png)

![image](https://user-images.githubusercontent.com/54981984/95892708-8c070500-0da4-11eb-85ee-3f87f337bd4a.png)

### Step 2: Create a Linux EC2 instance

### Step 3: Setting inbound of SG for both EC2 & RDS

#### Below shows the EC2 inbound rules

Add Postgresql as rule, as 172.31.30.104 IP of RDS( RDS IP can not be found in the console,we should find out using its endpoint url as below), 5432 as port no of RDS

![image](https://user-images.githubusercontent.com/54981984/95894981-91198380-0da7-11eb-89bf-f5355bcfd7ab.png)

![image](https://user-images.githubusercontent.com/54981984/95895214-f1a8c080-0da7-11eb-90bb-cfc80ffd1cc4.png)

#### Below shows the RDS inbound rules

#### Add Postgresql as rule, as 172.31.4.216 Private IP of EC2 ,5432 as port no of RDS

![image](https://user-images.githubusercontent.com/54981984/95895601-8ad7d700-0da8-11eb-9f4d-2c2cdbc4e66d.png)

### Step 4: ssh to EC2 instance in putty

#### Convert pem file to ppk file using putty 

![image](https://user-images.githubusercontent.com/54981984/95896320-b7402300-0da9-11eb-93f0-1e1f030824a3.png)

![image](https://user-images.githubusercontent.com/54981984/95896148-6cbea680-0da9-11eb-8486-ad395203b29c.png)

![image](https://user-images.githubusercontent.com/54981984/95896543-0423f980-0daa-11eb-9a4b-93210f7a70fd.png)

### Step 5: Login as ec2-user

![image](https://user-images.githubusercontent.com/54981984/95896656-3170a780-0daa-11eb-89be-68c5dcd9550a.png)

### Step 6: Copy paste the endpoint url of the RDS

### Step 7 : 'Type the command as below' 

        psql -h (endpoint url of RDS -p (port no: of postgresql) -U (Master username in RDS)
        
 Note: Commands will change based on the DB, In our case psql for postgresql
 
 ![image](https://user-images.githubusercontent.com/54981984/95897540-587ba900-0dab-11eb-9840-02d2491e2ca1.png)
 
 ![image](https://user-images.githubusercontent.com/54981984/95898095-27e83f00-0dac-11eb-80e2-980b15f407c6.png)
 
 ### Step 8: Connection established
 









