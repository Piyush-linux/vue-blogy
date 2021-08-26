# blogy
- [x] Create Blog
    - [x] clear con in form of create form
- [x] search blog

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
B: Nav
C: Blog

# A : A P P
data: 
    - blgs -> C     : blogs
meth:
    - B -> crtBlg   : Create blog
    - C -> delBlg   : Delete Blog
    - C -> viewBlg  : Zoom Blog
    - C -> updtBlg  :
    - (B -> srchBlg ) && -> C : 
    - C -> clMdl    : close model

# B : N A V
data:
    - New Blog > A
    - search > A > C
mth:
    - crtBlg: "> A"

# C : B L O G
data:
    A -> blgs : Display All blogs
    B -> search : Display Matching Char Only
    deleted Blog -> A : delete blogs

```
