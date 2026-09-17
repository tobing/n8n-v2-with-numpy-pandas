ARG N8N_VERSION
FROM n8nio/runners:${N8N_VERSION}

# Swith user to root
USER root

# Install Node.js packages for the JS runner
RUN cd /opt/runners/task-runner-javascript && pnpm add moment uuid axios cheerio form-data node-fetch csv-parse

# Install Python packages for the Python runner
RUN /opt/runners/task-runner-python/.venv/bin/python -m ensurepip --upgrade 
RUN /opt/runners/task-runner-python/.venv/bin/python -m pip install --no-cache-dir numpy pandas

# Replace n8n-task-runners.json to allow external packages
COPY n8n-task-runners.json /etc/n8n-task-runners.json

# Switch back to non-root user
USER runner
