# Netvault a Kubernetes based SFTP server

## Motivation
I wanted to make a folder accessible to a Linux VM running on my Mac. Since I did not want to use smb due security reasons and I was not able to use the built-in method my hypervisor offered, I thought let's try to build something using Kubernetes and the skills that I aquired so far.
After consulting my LLM, I decided to go with an SFTP server. 

## Implementation
I used an image from DockerHub: emberstack/sftp. I created a deployment and a service to expose the deployment. I also created a PersistentVolume and a PersistentVolumeClaim to store the data. I used a NodePort service to expose the SFTP server on port 30222. My Kubernetes cluster is running on a VPS. I use Tailscale to connect to the cluster from my Mac and the Linux VM.

## Lessons learned
- I know why a PersistentVolume and a PersistentVolumeClaim are needed, if you want to store data persistently.
- I learned how to setup permissions and ownership of files and folders in the shared folder to make them accessible to the SFTP user.
- I learned how to use a NodePort service to expose a deployment on a specific port.
- I learned that troubleshooting with an AI Agent can be misleading. You still have to think in your own.

## Next steps
- I want to use a StorageClass to dynamically provision PersistentVolumes. This is the more "Kubernetes way" of doing things as far as I understand it...
- I want to use a LoadBalancer service to expose the SFTP server. This is more secure than using a NodePort service.