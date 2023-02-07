ARG NODE_TAG=18-alpine

FROM node:${NODE_TAG} AS builder
# Check https://github.com/nodejs/docker-node/tree/b4117f9333da4138b03a546ec926ef50a31506c3#nodealpine to understand why libc6-compat might be needed.
RUN apk add --no-cache libc6-compat

WORKDIR /app

COPY package.json pnpm-lock.yaml ./
RUN npm add -g pnpm; \
  pnpm install --frozen-lockfile

COPY . .

RUN pnpm nx build admin --prod && pnpm prune --prod;

# =============================
FROM node:${NODE_TAG} AS production

ENV NEXT_TELEMETRY_DISABLED 1
ENV NODE_ENV production
ENV PORT 80

RUN addgroup -g 1001 -S nodejs
RUN adduser -S nextjs -u 1001

WORKDIR /app
COPY --from=builder --chown=nextjs:nodejs /app/package.json /app/pnpm-lock.yaml ./
COPY --from=builder --chown=nextjs:nodejs /app/node_modules ./node_modules
COPY --from=builder --chown=nextjs:nodejs /app/dist/apps/admin ./dist/apps/admin

USER nextjs

EXPOSE ${PORT}

CMD [ "sh", "-c", "npm start --prefix dist/apps/admin" ]