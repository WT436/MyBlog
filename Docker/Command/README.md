# Command

- Khi chạy lệnh docker --help chúng ta sẽ thấy một bảng các key và ý nghĩa của chúng sau đây là tất cả các lệnh trong đó giải thích và cách dùng chúng. Những lệnh nào hay dùng sẽ được đánh dấu * 
- Các lệnh viết tắt sẽ để trong () ví dụ vesion (-v)
- Syntax : docker (Component) (command) (arg)
- Chi tiết của các Component sẽ ở chung với folder này cứ thế mà triển thôi!

1. Management Commands: Các Component chính
  
  - builder      Manage builds <>
  - buildx       Build with BuildKit
  - compose      Docker Compose
  - config       Manage Docker configs
  - container*   Manage containers
  - context      Manage contexts
  - image*       Manage images
  - manifest     Manage Docker image manifests and manifest lists
  - network*     Manage networks
  - node*        Manage Swarm nodes
  - plugin*      Manage plugins
  - scan         Docker Scan
  - secret*      Manage Docker secrets
  - service*     Manage services
  - stack*       Manage Docker stacks
  - swarm*       Manage Swarm
  - system*      Manage Docker
  - trust        Manage trust on Docker images
  - volume*      Manage volumes

2. Commands: (các command của component)< có những component có cũng có những component thì không và cũng có những command đặc biệt chỉ dùng cho 1 component >
  
  - docker < component > attach   :  Attach local standard input, output, and error streams to a running container
  - docker < component > build    :  Build an image from a Dockerfile
  - docker < component > commit   :  Create a new image from a container's changes
  - docker < component > cp       :  Copy files/folders between a container and the local filesystem
  - docker < component > create   :  Create a new container
  - docker < component > diff     :  Inspect changes to files or directories on a container's filesystem
  - docker < component > events   :  Get real time events from the server
  - docker < component > exec     :  Run a command in a running container
  - docker < component > export   :  Export a container's filesystem as a tar archive
  - docker < component > history  :  Show the history of an image
  - docker < component > images   :  List images
  - docker < component > import   :   Import the contents from a tarball to create a filesystem image
  - docker < component > info     :   Display system-wide information
  - docker < component > inspect  :   Return low-level information on Docker objects
  - docker < component > kill     :   Kill one or more running containers
  - docker < component > load     :   Load an image from a tar archive or STDIN
  - docker < component > login    :   Log in to a Docker registry
  - docker < component > logout   :   Log out from a Docker registry
  - docker < component > logs     :   Fetch the logs of a container
  - docker < component > pause    :   Pause all processes within one or more containers
  - docker < component > port     :   List port mappings or a specific mapping for the container
  - docker < component > ps       :   List containers
  - docker < component > pull     :   Pull an image or a repository from a registry
  - docker < component > push     :   Push an image or a repository to a registry
  - docker < component > rename   :   Rename a container
  - docker < component > restart  :   Restart one or more containers
  - docker < component > rm       :   Remove one or more containers
  - docker < component > rmi      :   Remove one or more images
  - docker < component > run      :   Run a command in a new container
  - docker < component > save     :   Save one or more images to a tar archive (streamed to STDOUT by default)
  - docker < component > search   :   Search the Docker Hub for images
  - docker < component > start    :   Start one or more stopped containers
  - docker < component > stats    :   Display a live stream of container(s) resource usage statistics
  - docker < component > stop     :   Stop one or more running containers
  - docker < component > tag      :   Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
  - docker < component > top      :   Display the running processes of a container
  - docker < component > unpause  :   Unpause all processes within one or more containers
  - docker < component > update   :   Update configuration of one or more containers
  - docker < component > version  :   Show the Docker version information
  - docker < component > wait     :   Block until one or more containers stop, then print their exit codes
