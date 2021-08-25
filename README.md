# blogy

## Project setup
```
npm install
npm run serve
npm run build
```

- CRUD Blog
- Alert
- Tags
- Dark Mode
```yaml
# Component
A: App
B: Nav : create & search
C: Blog : Display / delete Blog

# A P P
data: 
    - blgs > C
meth:
    - crtBlg: < B
    - delBlg: < C
    - viewBlg: < C 
    - updtBlg: < C
    - srchBlg: < B && > C
# N A V
data:
    - New Blog > A
    - search > A > C
mth:
    - crtBlg: "> A"

# B L O G
data:
    -> blgs : Display All blogs
    -> search : Display Matching Char Only
    - deleted Blog > A

```
