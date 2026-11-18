# EBS
## WORKING WITH EBS
## NAME: SRI SAI SARAN G
## REG NO: 212225220103
## Aim
To create and configure an Amazon Elastic Block Store (EBS) volume, attach and mount it to an Amazon EC2 instance, create a snapshot backup, and restore the snapshot to a new EBS volume.

## Algorithm / Steps
Create a new Amazon EBS volume with a size of 1 GiB.

Select the same Availability Zone as the EC2 instance.

Attach the EBS volume to the EC2 instance using /dev/sdb.

Connect to the EC2 instance using AWS Systems Manager Session Manager.

Check the available storage using df -h.

Create an ext3 file system on the EBS volume.

Create the /mnt/data-store directory.

Mount the EBS volume to /mnt/data-store.

Configure /etc/fstab for automatic mounting.

Verify that the EBS volume is successfully mounted.

Create file.txt inside the mounted EBS volume.

Verify the contents of the created file.

Create an EBS snapshot named My Snapshot.

Delete file.txt from the original EBS volume.

Create a new EBS volume from the snapshot.

Attach the restored volume to the EC2 instance using /dev/sdc.

Create the /mnt/data-store2 directory.

Mount the restored volume to /mnt/data-store2.

Verify that file.txt has been successfully restored.

## Program
## 1. Check Available Storage
```
df -h
```
## 2. Create an ext3 File System
```
sudo mkfs -t ext3 /dev/sdb
```
## 3. Create a Mount Directory
```
sudo mkdir /mnt/data-store
```
## 4. Mount the EBS Volume
```
sudo mount /dev/sdb /mnt/data-store
```
## 5. Configure Automatic Mounting
```
echo "/dev/sdb   /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
```
## 6. View the File System Configuration
```
cat /etc/fstab
```
## 7. Verify the Mounted Volume
```
df -h
```
## 8. Create a File in the EBS Volume
```
sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
```
## 9. Read the File
```
cat /mnt/data-store/file.txt
```
## 10. Delete the File
```
sudo rm /mnt/data-store/file.txt
```
## 11. Verify File Deletion
```
ls /mnt/data-store/
```
## 12. Create a Mount Directory for the Restored Volume
```
sudo mkdir /mnt/data-store2
```
## 13. Mount the Restored EBS Volume
```
sudo mount /dev/sdc /mnt/data-store2
```
## 14. Verify Snapshot Restoration
```
ls /mnt/data-store2/
```
## Expected output:
```
file.txt
```
<img width="960" height="540" alt="Screenshot 2026-11-05 214848" src="https://github.com/user-attachments/assets/a4c26697-ab6a-4ddf-89cc-c3671cbf8daa" />
<img width="960" height="540" alt="Screenshot 2026-11-05 215111" src="https://github.com/user-attachments/assets/0082b709-fb9e-4d6b-b39a-41cbfa654406" />
<img width="960" height="540" alt="Screenshot 2026-11-05 215639" src="https://github.com/user-attachments/assets/600b6d3b-2034-4d8f-9eb6-fd2052528cbe" />
<img width="960" height="540" alt="Screenshot 2026-11-05 214418" src="https://github.com/user-attachments/assets/39cb60a7-2ac6-4128-b074-2dc9b01a2416" />
<img width="959" height="476" alt="Screenshot 2026-11-05 161208" src="https://github.com/user-attachments/assets/e6ba88f2-fd04-42d8-ad73-9e27bfb864b9" />



