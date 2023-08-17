# Use Kali Rolling release latest as the main base image
FROM kalilinux/kali-rolling:latest

LABEL maintainer="Sergey Zybnev <https://github.com/szybnev>"

WORKDIR /root

# Let's get those essentials
RUN apt-get clean &&  apt-get update &&  \
    apt-get full-upgrade -y &&  apt-get autoremove -y &&  \
    apt-get install -y curl \
                        build-essential \
                        python3 \
                        python3-pip \
                        python3-venv \
                        net-tools\
			whois \
			nano \
			vim \
			netcat-traditional \
			wget \
                        man-db \
			exploitdb \
			git \
                        fzf \
                        traceroute \
                        exa \
                        bat \
                        zip \
                        unzip \
                        ripgrep \
			libpcap-dev \
			iputils-ping \
			nmap masscan nikto \
			ffuf gobuster sqlmap && \
    apt-get clean  &&  rm -rf /var/lib/apt/lists/*

# Setup ENVs
ENV ls=exa \
    la="exa -lah" \
    laR="exa -lahR" \
    bat="batcat --theme Dracula --paging=never"

# Go, Go, Golang!
RUN wget https://go.dev/dl/go1.20.7.linux-amd64.tar.gz  &&  \
    tar -C /usr/local -xzf go*.tar.gz  &&  \
    rm go*.tar.gz
ENV PATH=$PATH:/usr/local/go/bin
ENV PATH=$PATH:/root/go/bin

# Rust, the language of legends
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
ENV PATH=$PATH:/root/.cargo/bin

# Project Discovery's goodies and install needed tools.
RUN go install github.com/xm1k3/cent@latest &&  \
    go install github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest &&  \
    go install github.com/projectdiscovery/shuffledns/cmd/shuffledns@latest &&  \
    go install github.com/projectdiscovery/notify/cmd/notify@latest &&  \
    go install github.com/projectdiscovery/dnsx/cmd/dnsx@latest &&  \
    go install github.com/projectdiscovery/httpx/cmd/httpx@latest
	
RUN go install github.com/projectdiscovery/katana/cmd/katana@latest &&  \
    go install github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest &&  \
    go install github.com/lc/gau/v2/cmd/gau@latest &&  \
    go install github.com/tomnomnom/anew@latest &&  \
    go install github.com/tomnomnom/fff@latest &&  \
    go install github.com/tomnomnom/waybackurls@latest && \
    git clone 'https://github.com/projectdiscovery/nuclei-templates' ~/nuclei-templates && \
    cent init &&  \
    git clone https://github.com/r0oth3x49/ghauri.git &&  cd ghauri &&  python3 -m pip install --upgrade -r requirements.txt &&  python3 setup.py install &&  cd  &&  \
    wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -  &&  \
    sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list' &&  \
    apt-get update  &&  apt-get install -y google-chrome-stable chromium && \
    rm -rf /var/lib/apt/lists/* 
    
RUN mkdir -p /root/.config/notify && touch ~/.ssh/authorized_keys

ENTRYPOINT ["/bin/bash"]
