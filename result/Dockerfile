FROM node:8.16.0-alpine
WORKDIR /app
COPY . .
RUN npm install  && \
    npm audit fix
ARG USER=resultuser
ENV HOME /home/$USER
RUN adduser -D $USER
RUN apk add --no-cache curl
HEALTHCHECK --interval=30s --timeout=10s --retries=2 --start-period=20s \
  CMD curl -f http://localhost:4000/ || exit 1
USER $USER
EXPOSE 4000
CMD npm start
