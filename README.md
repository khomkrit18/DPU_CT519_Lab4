# DPU_CT519_Lab4
DPU_CT519_Lab4_Docker_Compose_By_Khomkrit_Ngeonkham_645162010028

1.ให้ทำการ Dump Database ก่อนที่ Database Server
  1.1 เข้า mysql โดยใช้ใช้คำสั่ง ดังนี้
    mysql -u root -p
  1.2 ให้ใช้คำสั่ง mysqldump ดังนี้
    sudo mysqldump -u root -p -B CT519_Movie > my_data_645162010028.sql

2.ไปที่ VM DockerCompose
  2.1 ให้ทำการคัดลอกไฟล์ Backup Mysql มาไว้ที่เครื่องโดยใช้คำสั่ง
    scp kang@10.1.1.22:/home/kang/my_data_645162010028.sql . (เอาไฟล์ sql)
  2.2 ให้ทำการคัดลอกไฟล์ index.php มาไว้ที่เครื่องโดยใช้คำสั่ง
    scp kang@10.1.1.11:/var/www/html/index.php . (เอาไฟล์ Index.php)

3.ทำการสร้าง Folder DPU_CT519_Lab4 โดยใช้คำสั่ง
  mkdir DPU_CT519_Lab4

4.ทำการ cd เข้าไปที่ Folder DPU_CT519_Lab4 โดยใช้คำสั่ง
  cd DPU_CT519_Lab4

5.ทำการสร้าง Folder my-sql-backup และ www โดยใช้คำสั่ง
  mkdir my-sql-backup && mkdir www

6.ทำการย้ายไฟล์ index.php และ my_data_645162010028.sql โดยใช้คำสั่ง
  mv index.php www/index.php && mv my_data_645162010028.sql my-sql-backup/my_data_645162010028.sql

7.ทำการสร้างไฟล์ docker-compose.yaml โดยใช้คำสั่ง
  sudo nano docker-compose.yaml โดยใส่ข้อมูลตามที่อัพโหลดไว้

8.ทำการสร้างไฟล์ Dockerfile โดยใช้คำสั่ง
  sudo nano Dockerfile โดยใส่ข้อมูลตามที่อัพโหลดไว้

9.ทำการ Run DockerCompose โดยใช้คำสั่ง
  sudo docker compose up -d
  
หมายเหตุ
คำสั่งดู Docker ที่ทำงานอยู่
sudo docker network ls

สั่งหยุดการทำงาน Docker

sudo docker stop $(sudo docker ps -aq)
sudo docker rm $(sudo docker ps -aq)
คำสั่งหยุดการทำงาน Network Docker

sudo docker network rm dpu_ct519_lab4_Front-Net
sudo docker network rm dpu_ct519_lab4_Back-Net
คำสั่งขึ้น Docker ใหม่
sudo docker compose up -d

คำสั่งดูรายละเอียด Network

sudo docker network inspect dpu_ct519_lab4_Front-Net
sudo docker network inspect dpu_ct519_lab4_Back-Net
