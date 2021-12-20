# Uffizzi App  

**The primary REST API for creating and managing Previews**

While it provides a documented REST API for anyone to use, it's most valuable when used with the open-source [`uffizzi_cli`](https://github.com/UffizziCloud/uffizzi_cli).  

## Uffizzi Overview

Uffizzi is the Full-stack Previews Engine that makes it easy for your team to preview code changes before merging—whether frontend, backend or microserivce. Define your full-stack apps with a familiar syntax based on Docker Compose, then Uffizzi will create on-demand test environments when you open pull requests or build new images. Preview URLs are updated when there’s a new commit, so your team can catch issues early, iterate quickly, and accelerate your release cycles.  

[Learn more about full-stack previews and the broader goals of this project.](docs/continuous-previews.md)

## Getting started with Uffizzi  

The fastest and easiest way to get started with Uffizzi is via the fully hosted version available at https://uffizzi.com, which includes free plans for small teams and qualifying open-source projects.  

Alternatively, you can self-host Uffizzi via the open-source repositories available here on GitHub. The remainder of this README is intended for users interested in self-hosting Uffizzi or for those who are just curious about how Uffizzi works.

## Uffizzi Architecture  

Uffizzi consists of the following components:  

* Uffizzi App (this repository) - The primary REST API for creating and managing Previews  
* [Uffizzi Controller](https://github.com/UffizziCloud/uffizzi_controller) - A smart proxy service that handles requests from Uffizzi App to the Kubernetes API  
* [Uffizzi CLI](https://github.com/UffizziCloud/uffizzi_cli) - A command-line interface for Uffizzi App     
* [Uffizzi Dashboard](https://app.uffizzi.com) - A graphical user interface for Uffizzi App (not available for self-hosting)

To host Uffizzi yourself, you will also need the following external dependencies:  

 * Kubernetes (k8s) cluster  
 * Postgres database  
 * Redis cache  

## Controller Design  

This `uffizzi_app` acts as a REST API for [`uffizzi_cli`](https://github.com/UffizziCloud/uffizzi_app) and [`Uffizzi Dashboard`](https://app.uffizzi.com) interfaces. It requires [`uffizzi_controller`](https://github.com/UffizziCloud/uffizzi_controller) as a supporting service.  