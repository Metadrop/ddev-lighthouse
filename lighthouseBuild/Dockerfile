#ddev-generated
FROM node:18-bullseye-slim

# Set variable so puppeteer will not try to download chromium
ENV PUPPETEER_SKIP_DOWNLOAD=true
ENV PUPPETEER_EXECUTABLE_PATH=/usr/bin/google-chrome-stable

# Install utilities
RUN apt update --fix-missing && apt -y upgrade && apt install -y git wget gnupg

# Add sudo and sudoers in manner similar to other ddev containers
RUN apt install -y sudo; apt clean -qq && rm -rf /var/lib/apt/lists/*; echo "ALL ALL=NOPASSWD: ALL" > /etc/sudoers.d/ddev-lighthouse && chmod 440 /etc/sudoers.d/ddev-lighthouse

# Install latest chrome stable package.
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
RUN sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
RUN apt update \
    && apt install -y google-chrome-stable --no-install-recommends

# Install Lighthouse CI
RUN npm install -g @lhci/cli@0.13.0
RUN npm install -g lighthouse

# Install puppeteer
RUN npm install -g puppeteer

# Add custom entrypoint
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

# delete the default 'node' user with uid 1000 and add current ddev user
ARG username
ARG uid
ARG gid
RUN userdel -r node
RUN (groupadd --gid $gid "$username" || groupadd "$username" || true) && \
    (useradd -l -m -s "/bin/bash" --gid "$username" --comment '' --uid $uid "$username" --system --create-home || \
     useradd -l -m -s "/bin/bash" --gid "$username" --comment '' "$username" --system --create-home || \
     useradd -l -m -s "/bin/bash" --gid "$gid" --comment '' "$username" --system --create-home || \
     useradd -l -m -s "/bin/bash" --comment '' $username --system --create-home ) && \
    mkdir --parents /home/$username/reports && \
    chown --recursive $username:$username /home/$username

RUN cd /home/$username/reports && npm link puppeteer
USER $username

WORKDIR /home/$username/reports
CMD [ "lhci", "--help" ]

