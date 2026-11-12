---
section: performance
---
- **A steady frame makes no bind groups** (zgx-gpu): a frame with a backdrop blur made its blur's bind groups (up to five) and two viewport groups anew each frame, each a trip through wgpu's validation, because they bound ranges of that frame's vertex buffer. Those ranges are now bound at dynamic offsets and the groups kept, and Direct3D 11 keeps its blur records buffers from frame to frame. A scrolled frame under a frosted panel makes about 96 fewer allocations (of some 490).
