# orthanc-ohifViewer-docker

安装部署orthanc

    //拉取镜像
	docker pull jodogne/orthanc-plugins
	//创建数据和配置文件目录
	mkdir /mnt/orthanc/config/
	mkdir /mnt/orthanc/db/
	//拷贝orthanc.json 到配置目录
	cp ./orthanc.json /mnt/orthanc/config/orthanc.json
	//启动docker
	docker run -itd  --name orthanc -p 4242:4242 -p 8042:8042 --restart=always --privileged=true -v /mnt/orthanc/db/:/var/lib/orthanc/db/ -v /mnt/orthanc/config/orthanc.json:/etc/orthanc/orthanc.json  jodogne/orthanc-plugins

安装部署ohif

    //拉取镜像
    docker pull ohif/viewer
	//创建配置目录
	mkdir /mnt/ohif/config
	//拷贝配置文件到配置目录
	copy ./app-config.js /mnt/ohif/config/app-config.js
	copy ./default.conf /mnt/ohif/config/default.conf
	//启动docker
	docker run -itd --name ohif -p 3000:80 -v /mnt/ohif/config/default.conf:/etc/nginx/conf.d/default.conf -v /mnt/ohif/config/app-config.js:/usr/share/nginx/html/app-config.js ohif/viewer:latest































