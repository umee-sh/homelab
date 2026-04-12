FROM debian:13.4 AS build

ARG PHANPY_VERSION="2026.02.24.48b2cf7"
ARG PHANPY_DEFAULT_INSTANCE="hollo.umee.sh"
ARG PHANPY_DEFAULT_LANG="ja"

RUN apt-get update && \
  apt-get install -y --no-install-recommends curl git ca-certificates && \
  curl -fsSL https://deb.nodesource.com/setup_24.x | bash - && \
  apt-get install -y nodejs && \
  rm -rf /var/lib/apt/lists/*

RUN git clone --depth 1 -b $PHANPY_VERSION https://github.com/cheeaun/phanpy.git /root/phanpy && \
  cd /root/phanpy && \
  npm install && npm run build



FROM nginx:1.29.8-alpine

COPY --from=build /root/phanpy/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
