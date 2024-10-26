# How to Use Veracrypt GUI on Unraid

This guide will walk you through setting up and using the Veracrypt GUI Docker container on your Unraid server.

## 📖 Table of Contents
- [Initial Setup](#initial-setup)
- [Accessing the GUI](#accessing-the-gui)
- [Creating and Mounting Volumes](#creating-and-mounting-volumes)
- [SMB Share Configuration](#smb-share-configuration)
- [Troubleshooting](#troubleshooting)

## Initial Setup

[Screenshots will be added here showing the steps]

1. After installing the template, navigate to your Docker settings
2. Locate and click on the Veracrypt container
3. Configure the following paths:
   - `/mnt/user/appdata/veracrypt-gui` for configuration
   - `/mnt/user/containers` for container storage
   - `/mnt/disks` for mounted volumes

## Accessing the GUI

1. Once the container is running, access the web interface at:
   ```
   http://[YOUR-UNRAID-IP]:5800
   ```
2. You should see the Veracrypt GUI interface in your browser

## Creating and Mounting Volumes

![Screenshot 2024-10-27 004815](https://github.com/user-attachments/assets/b24fd4d5-42d0-4a26-b13b-1dbc9f5db62e)
![Screenshot 2024-10-27 004910](https://github.com/user-attachments/assets/92e5b2c2-20cf-4aec-8c8e-8e0e669d15f4)
![Screenshot 2024-10-27 004922](https://github.com/user-attachments/assets/f3458b39-7de8-45d9-bc46-5ff19ca1ad1f)
![Screenshot 2024-10-27 004958](https://github.com/user-attachments/assets/651e817d-f549-4819-a26d-8b00df35bc95)
![Screenshot 2024-10-27 005019](https://github.com/user-attachments/assets/544aa70a-a3a7-4f2f-acd5-eacab64551b2)
![Screenshot 2024-10-27 005026](https://github.com/user-attachments/assets/2a34dee1-5518-43a3-8e26-fc312e41c775)
![Screenshot 2024-10-27 005103](https://github.com/user-attachments/assets/ea8a1474-faaf-4b48-90bf-c5725a86030b)
![Screenshot 2024-10-27 005119](https://github.com/user-attachments/assets/5a904aac-765d-4a8a-8c23-3473346b421d)
![Screenshot 2024-10-27 005148](https://github.com/user-attachments/assets/5e3cae4c-0ca8-4664-a746-875f964db4ab)
![Screenshot 2024-10-27 005347](https://github.com/user-attachments/assets/de8f347c-379d-45dc-976c-3f6894894d5f)
![Screenshot 2024-10-27 005411](https://github.com/user-attachments/assets/521a6e8e-cff4-46b0-83bc-f62c1f47e44d)
![Screenshot 2024-10-27 005437](https://github.com/user-attachments/assets/e923ec64-2e1a-401d-82b8-6689678bff39)

1. Using the GUI interface:
   - Create new volume or select existing one
   - Choose mount location
   - Enter credentials
2. Mounted volumes will be available in the `/mnt/disks` directory

## SMB Share Configuration

To share your Veracrypt volumes over the network, add the following configuration to your Unraid SMB settings:

```ini
[veracrypt1]
      path = /mnt/disks/veracrypt1
      comment = 
      browseable = yes
      writeable = no
      read list = 
      write list = %%username%%
      valid users = %%username%%
      case sensitive = auto
      preserve case = yes
      short preserve case = yes
```

### Configuration Breakdown:
- `path`: Points to your mounted Veracrypt volume
- `browseable`: Makes the share visible in network browsing
- `writeable`: Set to 'no' by default for security
- `write list`: Allows specified users to write to the share
- `valid users`: Controls who can access the share
- `case sensitive`: Handles file name case sensitivity

### Setting Up the Share:

1. Navigate to Unraid's SMB settings
2. Add the above configuration
3. Replace `%%username%%` with your actual username
4. Save and restart the SMB service
5. Now you should see your share on your server

![Screenshot 2024-10-27 010340](https://github.com/user-attachments/assets/fa21607c-559d-4988-af5a-5bb39dfb0ece)


## Security Considerations

1. **Access Control**:
   - Use strong passwords for Veracrypt volumes
   - Limit network share access to specific users
   - Consider using read-only shares when possible

2. **Network Security**:
   - Use encrypted connections when possible
   - Limit access to trusted network segments
   - Regularly review access logs

## Troubleshooting

### Common Issues and Solutions:

1. **Mount Problems**:
   - Verify container permissions
   - Check path configurations
   - Ensure correct credentials
   - Make sure image is mount in Veracrypt

2. **SMB Access Issues**:
   - Confirm user permissions
   - Verify network connectivity
   - Check Unraid's SMB logs

3. **GUI Access Problems**:
   - Verify container is running
   - Check port configuration
   - Review container logs

---

For more detailed information, visit the [main README](./README.md).
