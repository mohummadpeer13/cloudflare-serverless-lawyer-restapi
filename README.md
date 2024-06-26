# Lawyer-restapi project 

  * Cloudflare workers
  * Prisma cloud
  * Mongo DB Atlas 
  * REST API
  
# Sources

  * https://www.prisma.io/docs/guides/deployment/edge/deploy-to-cloudflare-workers
  * https://hono.dev/getting-started/cloudflare-workers
  
# Create Project With Wrangler

  * wrangler init serverless-lawyer
  
  - hello world project
  - typescript project / yes
  - deploy app / no 
  
# Create Github Repository
  
  * create github repository an clone this
  * add project to repository
  * push project on github
 
# Install Hono

  * npm install hono
  * npm install @hono/node-server

# Create Prisma Project

  * npm install -D prisma
  * npx prisma init
  * add schema in /prisma/schema.prisma
  
  
  generator client {
  
    provider = "prisma-client-js"
    
  }
  

  datasource db {
  
    provider = "mongodb"
  
    url      = env("DATABASE_URL")
  
  }

  model User {
  
    id         String @id @default(auto()) @map("_id") @db.ObjectId
  
    role       Role
  
    firstName  String
  
    lastName   String
  
    email      String @unique
  
    password   String
  
    address    Json
  
    createdAt  DateTime @default(now())
  
    updatedAt  DateTime @updatedAt
  
  }

  enum Role {
  
    User
  
    Admin
  
    Manager
  
  }
  
# Push project to github repository with new prisma schema

  * You're ready to import your project into the Prisma Data Platform.
  
# Import your Project into the Prisma Data Platform

  * New project
  * Enter Mongo DB URL
  * Statics IPs => Disabled (Make sure on Mongo Atlas ips restriction allow all)
  * Choose Data Proxy Region => eu-central-1 (Frankfurt)
  
  * Synchronise your project with github account (repository and branch)
  * Link Prisma Schema => schema.prisma folder (default)
  * Create a new connection string => generate prisma url
  * Validate configuration
  
  * In .env add prisma url
      
      DATABASE_URL="xxxxxxxx"
    
  * In wrangler.toml add prisma url
      
      [vars]
      
      DATABASE_URL = "prisma://aws-us-east-1.prisma-data.com/?api_key=•••••••••••••••••"
      
# Generate a Prisma Client

  * npx prisma generate --data-proxy
  
# Develop the Cloudflare Worker function

 * dev your rest api

# Publish to Cloudflare Workers Online

  * npm run deploy
  
# ENJOY
