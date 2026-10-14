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

# The base image is Debian 11 (bullseye), which is EOL and has been moved to
# archive.debian.org. Point apt there so packages can still be installed.
RUN if grep -q bullseye /etc/os-release; then \
      sed -i -E 's#http://deb.debian.org/debian(-security)?#http://archive.debian.org/debian\1#' /etc/apt/sources.list; \
    fi

# Add sudo and sudoers in manner similar to other ddev containers
RUN apt-get update && apt-get install -y sudo && mkdir -p /etc/sudoers.d && echo "ALL ALL=NOPASSWD: ALL" > /etc/sudoers.d/ddev-lighthouse && chmod 440 /etc/sudoers.d/ddev-lighthouse
RUN mkdir --parents /home/$username/reports && chown --recursive $username:$username /home/$username

# Install mkcert
RUN apt-get install -y curl libnss3-tools && curl -fsSL -o /usr/local/bin/mkcert "https://dl.filippo.io/mkcert/latest?for=linux/amd64" && chmod +x /usr/local/bin/mkcert

# Setup ddev user name and folder.
USER $username
WORKDIR /home/$username/reports
