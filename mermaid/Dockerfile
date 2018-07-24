FROM node:latest

WORKDIR /data
RUN mkdir -p /var/lib/mermaid \
        && apt update && apt install -y --no-install-recommends \
                libx11-xcb1 \
                libxcomposite1 \
                libxcursor1 \
                libxdamage1 \
                libxi6 \
                libxtst6 \
                libnss3 \
                libcups2 \
                libxss1 \
                libxrandr2 \
                libasound2 \
                libatk1.0-0 \
                libatk-bridge2.0-0 \
                libgtk-3-0 \
        && rm -rf /var/lib/apt/lists/* \
        && yarn global add mermaid mermaid.cli
COPY ./puppeteer-config.json /var/lib/mermaid

ENTRYPOINT [ "/usr/local/bin/mmdc", "-p", "/var/lib/mermaid/puppeteer-config.json" ]
CMD []
