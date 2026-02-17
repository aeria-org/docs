# Troubleshooting

## Types from `aeria-sdk` differ from schema definition

Supposing the project is a monorepo (as in the Quickstart or created with `create-aeria-app`), make sure the versions of Aeria dependencies in API and frontend match. If, for some reason, the version of `aeria-ui` is bumped but `aeria` or `aeria-sdk` versions are not, there will be a conflict in internal types.

How to verifiy this is the case (run in both API and frontend folders):

```sh
npm explain @aeriajs/types
```

If versions differ, then you must update or pin the dependencies to use the same version.

