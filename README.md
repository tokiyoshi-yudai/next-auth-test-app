## Getting Started

### 1. Clone the repository and install dependencies

```
git clone git@github.com:tokiyoshi-yudai/next-auth-test-app.git
cd next-auth-test-app.git
npm install
```

### 2. Configure your local environment

Copy the .env.local.example file in this directory to .env.local (which will be ignored by Git):

```
cp .env.local.example .env.local
```

Add details for one or more providers (e.g. Google, Twitter, GitHub, Email, etc).

Setup prisma-accelerate-local
*You can see more details at https://github.com/node-libraries/prisma-accelerate-local.

```
npx prisma-accelerate-local -s secret -m postgresql://postgres:password@localhost:5432/postgres

# Output
eyJhbGciOiJIUzI1NiJ9.eyJkYXRhc291cmNlVXJsIjoiYSIsImlhdCI6MTcwMzY2NDg1NywiaXNzIjoicHJpc21hLWFjY2VsZXJhdGUifQ.4ruaA1RAT9cD3PACSEVIdUs3i2exKkMpNYGks3hyos4
```

Modify your .env.local

```
# .env.local

DATABASE_URL="prisma://localhost:4000/?api_key=Output(ex: eyJhbGciOiJIUzI1NiJ9.eyJkYXRhc291cmNlVXJsIjoiYSIsImlhdCI6MTcwMzY2NDg1NywiaXNzIjoicHJpc21hLWFjY2VsZXJhdGUifQ.4ruaA1RAT9cD3PACSEVIdUs3i2exKkMpNYGks3hyos4)"
NODE_TLS_REJECT_UNAUTHORIZED="0"
# To remove the NODE_TLS_REJECT_UNAUTHORIZED warning
NODE_NO_WARNINGS="1"
```

### 3. Migrate DB

```
./node_modules/.bin/dotenv -e .env.local -- npx prisma migrate dev
```

You can see database dashboard

```
npx prisma studio
```

### 4. Start the application

To run your site locally, use:

```
# start server of prisma-accelerate-local
npx prisma-accelerate-local postgresql://postgres:password@localhost:5432/postgres -p 4000

# start application server
npm run dev
```

To run it in production mode, use:

Shoud setup accelerate, look up https://www.prisma.io/docs/accelerate 

```
npm run build
npm run start
```

```
npx prisma studio
```


Reference: https://github.com/nextauthjs/next-auth/tree/a14fe18eb9626f4179cf7a510721f874f240cdc4/apps/examples/nextjs

License: ISC
