---
section: performance
---
- **Rows scrolled in reuse the lists rows scrolled out leave** (zgx): a virtualized list scrolling fast made and freed, a row a frame, each node's children list, each container's list of where its children go, and each view's list of child views, and copied every node's children to tell a renderer which nodes went. A removed subtree is now walked into the list it is told in, and the emptied lists of removed nodes and mounted views go to the nodes and views made next. They are kept only while rows come and go: eight frames with none let them go, so a scene at rest holds no more than before. A fast scroll through deep rows (scroll-glass) allocates 358 times a frame where it did 466.
