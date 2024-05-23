#ddev-generated
ARG BASE_IMAGE
FROM $BASE_IMAGE

# Add custom entrypoint
COPY ./entrypoint.sh /entrypoint.sh

# Swap to root user.
USER root
RUN chmod +x /entrypoint.sh

# delete the default 'node' user with uid 1000 and add current ddev user
ARG username
ARG uid
ARG gid
RUN userdel -r node
RUN (groupadd --gid $gid "$username" || groupadd "$username" || true) && (useradd  -l -m -s "/bin/bash" --gid "$username" --comment '' --uid $uid "$username" || useradd  -l -m -s "/bin/bash" --gid "$username" --comment '' "$username" || useradd  -l -m -s "/bin/bash" --gid "$gid" --comment '' "$username" || useradd -l -m -s "/bin/bash" --comment '' $username )

# Add sudo and sudoers in manner similar to other ddev containers
RUN apt update --fix-missing; apt install -y sudo; mkdir /etc/sudoers.d; echo "ALL ALL=NOPASSWD: ALL" > /etc/sudoers.d/ddev-lighthouse && chmod 440 /etc/sudoers.d/ddev-lighthouse

RUN mkdir --parents /home/$username/reports && chown --recursive $username:$username /home/$username

# Setup ddev user name and folder.
USER $username
WORKDIR /home/$username/reports
