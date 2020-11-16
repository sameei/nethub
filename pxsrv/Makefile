
cert:
	mkdir cert
	openssl req -new -newkey rsa:2048 -sha256 -days 1095 -nodes \
		-x509 -keyout cert/key.pem -out cert/ca.pem \
		-subj '/CN=squid-proxy/O=NULL/C=AU'
	chmod 600 cert/key.pem
	openssl x509 -in cert/ca.pem -outform DER -out cert/ca.der
	cat cert/key.pem cert/ca.pem >> cert/stunnel.pem
.PHONY: cert_rm
cert_rm:
	rm -rf ./cert


.PHONY: build
build:
	docker build --tag=pxsrv .

