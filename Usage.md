Clone the repo:

		git clone https://github.com/lparis/kuard.git

Create the binary:

		make

Save the existing Dockerfile as Dockefile-orig.

Create the new Dockerfile:

		FROM alpine
		COPY bin/blue/amd64/kuard /kuard
		ENTRYPOINT [ "/kuard" ]

Build the image:

		docker build -t kuard-amd64:blue .

Tag the image:

		docker tag kuard-amd64:blue demo.goharbor.io/tanzu/kuard:tanzu

Push the image to the registry at https//demo.goharbor.io/harbor/projects/14/tanzu

		docker push demo.goharbor.io/tanzu/kuard:tanzu

Pull the image:

		docker pull demo.goharbor.io/tanzu/kuard:tanzu

Run the image:

		docker run --rm -ti --name kuard --publish 8080:8080 kuard:tanzu

Verify: http://localhost:8080


		

