---
marp: true
theme: default
paginate: true
header: ![height:40px](https://quantstack.net/img/logo.svg)
footer: ![height:20px](img/twitter.svg) ![height:20px](img/github.svg) @JohanMabille @ThorstenBeier @QuantStack
style: @import url('https://unpkg.com/tailwindcss@^2/dist/utilities.min.css');
---

<style>
section::after {
  content: attr(data-marpit-pagination) '/' attr(data-marpit-pagination-total);
}
img[alt~="center"] {
  display: block;
  margin: 0 auto;
}
</style>

![bg fit right:30%](https://jupyter.org/assets/homepage/main-logo.svg)

# xeus kernels in the browser

## JupyterCon 2023

---

# About

<div class="grid grid-cols-2 gap-4">
<div>

## Johan Mabille

- Technical Director at QuantStack
- Jupyter Distinguished Contributor
- Co-authored the xeus stack, the debugger in Jupyter
- Leads the development of mamba

</div>
<div>

## Thorsten Beier

- Scientific Software Developer at QuantStack
- Co-authored the emscripten-forge stack
- Co-authored OpenGM2, author of Nifty
- Contributor to VIGRA, a generic image processing library

</div>
</div>

---

# Jupyter architecture

![h:400px center](https://xeus.readthedocs.io/en/latest/_images/jupyter_archi.svg)

- A well-specified protocol built upon web standards
- Implemented for more than 40 languages

---

# Writing kernels for Jupyter

- Write from scratch in your favorite language
- Adopt the kernel wrapper approach, based on ipykernel
- Build upon xeus, a native implementation of the protocol

---

# The xeus galaxy

- xeus: a native implementation of the Jupyter Kernel Protocol
- xeus + interpreter + glue code = Jupyter kernel
- xeus-cling (C++), xeus-python, xeus-sql, xeus-lua, etc...
- xwidgets: a native backend for the Jupyter interactive widgets

---

# Implementing a kernel

![bg fit right](img/echo-kernel.png)

---

# The Jupyter kernel protocol

Clients and kernels communicate (over the network) through 5 channels:
- Shell: code execution, code completion
- Control: stop and restart, kernel info, debugging
- stdin: input request
- IOPub: broadcast channel to publish results and kernel state
- Heartbeat: to check the kernel is still alive

ZeroMQ provides the low-level transport layer over which the messages are sent.

---

# Architecture of xeus (before)

![h:500px center](img/xeus_archi_previous.svg)

---

# Architecture of xeus (now)

![h:500px center](img/xeus_archi.svg)