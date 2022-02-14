# Image docker
[Nguồn](https://docs.docker.com/engine/reference/commandline/image/)
1. Syntax
  
2. Command (để hiển thị danh sách này chạy lệnh cha docker image)
  - build       Build an image from a Dockerfile 

    - xây dựng image từ docker file hoặc từ url hoặ từ 1 path nhất định
    - docker image build [OPTIONS] PATH | URL | -
    - Git repositories tham khảo [Tại đây](https://docs.docker.com/engine/reference/commandline/build/#git-repositories)
    
  - history     Show the history of an image
  
    - syntax : docker image history [OPTIONS] IMAGE
    - option : định dạng nếu null thì nó show tất [Ở Đây](https://docs.docker.com/engine/reference/commandline/image_history/#options)
    - IMAGE  : Id của image

  - import      Import the contents from a tarball to create a filesystem image

    - Chạy một file tar trên một máy mới để xây dự 1 image
    - Tham khảo [tại đây](https://docs.docker.com/engine/reference/commandline/image_import/)
    - Syntax : docker image import [OPTIONS] file|URL|- [REPOSITORY[:TAG]]
    - Còn lấy cái file quỷ này ở đâu thì sẽ không nói ở đây

  - inspect     Display detailed information on one or more images

    - Hiển thị thông tin chi tiết trên một hoặc nhiều image (json)
    - Syntax docker image inspect [OPTIONS] IMAGE [IMAGE...]
    - Tham khảo [tại đây](https://docs.docker.com/engine/reference/commandline/image_inspect/)

  - load        Load an image from a tar archive or STDIN

    - Tải image từ kho lưu trữ tar hoặc STDIN
    - Tham khảo [tại đây](https://docs.docker.com/engine/reference/commandline/image_load/)

  - run 
    
    - docker run < IMAGE ID >
    - chạy image thành 1 container

  - ls          List images

    - hiển thị danh sách image đang có trong docker
    - Tham khảo [tại đây](https://docs.docker.com/engine/reference/commandline/image_ls/)
    - có thể viết tắt thành docker images
    - TAG : hiển thị tag image 1 cách hợp lý
    - Image ID : Xác định duy nhất image
    - Created  : số ngày image  tồn tại
    - Virtual Size (Size) : kích thước 
  
  - prune       Remove unused images

    - Xóa hình ảnh không sử dụng
    - Tham khảo [tại đây](https://docs.docker.com/engine/reference/commandline/image_prune/)
    - docker image prune [OPTIONS]

  - pull        Pull an image or a repository from a registry

    - Kéo một image hoặc một repository từ registry
    - Tham khảo [tại đây](https://docs.docker.com/engine/reference/commandline/image_pull/)

  - push        Push an image or a repository to a registry

    - đẩy một image hoặc một repository lên registry
    - Tham khảo [tại đây](https://docs.docker.com/engine/reference/commandline/image_push/)

  - rm          Remove one or more images

    - Xóa một hoặc nhiều Image
    - docker image rm [OPTIONS] IMAGE [IMAGE...]
    - Tham khảo [tại đây](https://docs.docker.com/engine/reference/commandline/image_rm/)

  - save        Save one or more images to a tar archive (streamed to STDOUT by default)

    - Lưu một hoặc nhiều Imagevào kho lưu trữ tar (được truyền trực tuyến đến STDOUT theo mặc định)
    - Docker image save [OPTIONS] IMAGE [IMAGE...]
    - Tham khảo [tại đây](https://docs.docker.com/engine/reference/commandline/image_save/)
    
  - tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE

    - Tạo thẻ TARGET_IMAGE đề cập đến SOURCE_IMAGE
    - docker image tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]
    - Tham khảo [tại đây](https://docs.docker.com/engine/reference/commandline/image_tag/)