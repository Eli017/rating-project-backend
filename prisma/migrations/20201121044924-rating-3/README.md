# Migration `20201121044924-rating-3`

This migration has been generated by Eli Sokeland at 11/20/2020, 11:49:24 PM.
You can check out the [state of the schema](./schema.prisma) after the migration.

## Database Steps

```sql

```

## Changes

```diff
diff --git schema.prisma schema.prisma
migration 20201121042534-rating-2..20201121044924-rating-3
--- datamodel.dml
+++ datamodel.dml
@@ -7,9 +7,9 @@
 }
 datasource db {
   provider = "postgresql"
-  url = "***"
+  url = "***"
 }
 model User {
   id        String   @id @default(cuid())
@@ -21,9 +21,8 @@
   lastname  String?
   role      Role
   reviewed  Rating?  @relation("reviewed")
   reviewer  Rating?  @relation("reviewer")
-  ratings   Rating[]
 }
 model Rating {
   id         String   @id @default(cuid())
@@ -33,12 +32,10 @@
   reviewedID String   @unique
   category   Category
   rating     Int
   notes      String?
-  userId     String?
   reviewed   User     @relation("reviewed", fields: [reviewedID], references: [id])
   reviewer   User     @relation("reviewer", fields: [reviewerID], references: [id])
-  User       User?    @relation(fields: [userId], references: [id])
 }
 enum Role {
   ADMIN
```


