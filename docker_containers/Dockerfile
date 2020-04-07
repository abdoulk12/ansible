FROM ubuntu:16.04

RUN apt-get update && apt-get install -y openssh-server \
  && mkdir /var/run/sshd \
  && mkdir /root/.ssh && chmod 0700 /root/.ssh \
  && echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC6EpvxW3nwPvkCq1pS4E9fz/7zzI7CYlZtExYNsYbQO+1Ptp+XnzUVwSXoDJbA2qK1mQsB8ZXC5sMz7/+tLu6Oe0+ur2BUB/RSCJhT75g5DyUpRg4KL7K0lLW3wUS5kXI5GxkePqNBiWRvePnC9wDMdFuplu2aCLbC+GCxFvK1afSOeLamGCRUEPFDATdK2Wr9tpjqJiGJb0oNZMNEhwb1lLv5poRiKRstkPFSMTSaJimXHZx0CN768sKMj2XcV8dbhInfqwrbvKcNmH7lDDnCtYCcBU/xN8lVlN5aeN2S74ATc9RTjCF82i319DnZEgG+LfuiQpGCwAXBonqodtpd abdou@DESKTOP-4CCBMUG" > /root/.ssh/authorized_keys \
  && sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config \
  && sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd \
  && echo "export VISIBLE=now" >> /etc/profile 

ENV NOTVISIBLE "in users profile"

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
