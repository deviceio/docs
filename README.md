# Deviceio Real-Time Orchestration

The Deviceio Ecosystem is comprised of a suite of tools enabling sysadmins, developers and power users real-time orchestration capabilities of their devices. The core of this ecosystem are two software components the Hub and Agent:

| Hub | Agent |
| :--- | :--- |
| Accepts incoming Agent connections and exposes an HTTP API. | Connects out to a specified Hub exposing orchestration primatives. |

The Hub and Agent components leverage three principle concepts in the ecosystem:

* **Real-Time Streaming**
* **Orchestration Primatives**
* **Integrations**

# Real-Time Streaming

Most computer orchestration systems are built around a request/response paridigm in which you must await the completion of the request and await the return of the full response before you can read any data about an operation. Deviceio while retaining the Request/Response paradigm, supports real-time streaming of request and/or response bodies via HTTP chunked transfer encoding.



Many operations against a device through the Hub's HTTP API happen in real-time. Such operations such as reading/writing files or sending/recieving network connection data happen by streaming input/output via independant HTTP chunked encoded request or response streams. This means integrations can obtain the full power of Orchestration Primatives such as streaming a file write incrementally or streaming a file read incrementally, or consuming a process's stdout and stderr streams in real-time while simultantiously streaming data to the process's stdin!

# Orchestration Primatives

Accessing a device through the Hub's HTTP API gives you real time capability to a number of orchestration primitives normally found within a traditional computer operating system. Some examples of orchestration primitives might be:

* filesystem

  * streaming file reads
  * streaming file writes

  * creating files

  * deleting files

  * hashing files
  * listing directories

* processes

  * creating processes
  * streaming stdin, stdout and stderr

* networking
  * creating TCP/UDP connections
  * streaming socket tx/rx data
  * making HTTP calls
* hardware
  * streaming audio devices
  * streaming video devices
  * streaming input devices
  * accessing GPIO pins

The principle is that software agents should only expose primitive operations instead of embedding business-specific logic into the agent itself. This keeps the agent simple and small and most importantly generic in regard to the specific integration being performed. By combining multiple primitive operations an integration can create infrastructure capabilities that other agent-based systems cannot, such as: configuration management, configuration database, filesystem enforcement, socket tunneling etc.

# Integrations

Integrations provide the business-specific functionality via a software designed to interact with devices directly through the Hub HTTP API. The Deviceio Ecosystem provides many integrations for business-specific functionality but custom integrations are 

