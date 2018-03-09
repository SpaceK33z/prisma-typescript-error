<h1 align="center"><strong>Boilerplate for a Basic GraphQL Server w/ TypeScript</strong></h1>

This repository is to demo TypeScript error TS2416 in `src/generated/prisma.ts` when `"strictFunctionTypes": true` is used in `tsconfig.json`.

It is exactly the same as the "basic graphql server w/ typescript" boilerplate, except the config option mentioned above and the addition of a `yarn build` command that runs `tsc`.

Run `yarn && prisma deploy && yarn build` to build the application.

The output is:

```
src/generated/prisma.ts(595,3): error TS2416: Property 'query' in type 'Prisma' is not assignable to the same property in base type 'Prisma'.
  Type 'Query' is not assignable to type 'QueryMap'.
    Property 'post' is incompatible with index signature.
      Type '(args: { where: PostWhereUniqueInput; }, info?: string | GraphQLResolveInfo) => Promise<Post>' is not assignable to type '(args?: { [key: string]: any; }, info?: string | GraphQLResolveInfo) => Promise<any>'.
        Types of parameters 'args' and 'args' are incompatible.
          Type '{ [key: string]: any; }' is not assignable to type '{ where: PostWhereUniqueInput; }'.
            Property 'where' is missing in type '{ [key: string]: any; }'.
src/generated/prisma.ts(602,3): error TS2416: Property 'mutation' in type 'Prisma' is not assignable to the same property in base type 'Prisma'.
  Type 'Mutation' is not assignable to type 'QueryMap'.
    Property 'createPost' is incompatible with index signature.
      Type '(args: { data: PostCreateInput; }, info?: string | GraphQLResolveInfo) => Promise<Post>' is not assignable to type '(args?: { [key: string]: any; }, info?: string | GraphQLResolveInfo) => Promise<any>'.
        Types of parameters 'args' and 'args' are incompatible.
          Type '{ [key: string]: any; }' is not assignable to type '{ data: PostCreateInput; }'.
            Property 'data' is missing in type '{ [key: string]: any; }'.
src/index.ts(40,34): error TS2345: Argument of type '{ typeDefs: string; resolvers: { Query: { feed(parent: any, args: any, context: Context, info: an...' is not assignable to parameter of type 'Props'.
  Types of property 'resolvers' are incompatible.
    Type '{ Query: { feed(parent: any, args: any, context: Context, info: any): Promise<Post[]>; drafts(par...' is not assignable to type 'IResolvers'.
      Property 'Query' is incompatible with index signature.
        Type '{ feed(parent: any, args: any, context: Context, info: any): Promise<Post[]>; drafts(parent: any,...' is not assignable to type 'GraphQLScalarType | (() => any) | IResolverObject'.
          Type '{ feed(parent: any, args: any, context: Context, info: any): Promise<Post[]>; drafts(parent: any,...' is not assignable to type 'IResolverObject'.
            Property 'post' is incompatible with index signature.
              Type '(parent: any, { id }: { id: any; }, context: Context, info: any) => Promise<Post>' is not assignable to type 'GraphQLFieldResolver<any, any, { [argName: string]: any; }> | IResolverOptions'.
                Type '(parent: any, { id }: { id: any; }, context: Context, info: any) => Promise<Post>' has no properties in common with type 'IResolverOptions'.
```

The expect result is that there are no TypeScript errors.