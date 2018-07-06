docker  build -t liyongjian5179/jenkins .

docker run -d --restart=always -m=5120m -p 10.10.10.20:8280:8080 -v /opt/mavenStorage:/root/.m2/repository -v /home/lyj/lyj_jenkins_home:/var/jenkins_home -v /home/lyj/lyj_jenkins/tomcat-logs:/opt/tomcat/logs --name lyj_jenkins liyongjian5179/jenkins

#为java添加必要的类
docker cp jfxrt.jar wee_jenkins:/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.131-2.b11.el7_3.x86_64/jre/lib
docker cp jfxrt.jar wee_jenkins:/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.131-2.b11.el7_3.x86_64/jre/lib/ext

server {
	listen 80;
	server_name 123.com;
	location / {
		root	/usr/share/nginx/html;
		index	index.html index.html;
	}
	
	location /jenkins/ {
		proxy_pass http://192.168.112.129:1222;
# 	        rewrite .* http://192.168.112.129:8082 break;

	}
}
