# syntax=docker/dockerfile:1.4

ARG OS_DISTRO=oraclelinux
ARG OS_RELEASE=8

FROM $OS_DISTRO:$OS_RELEASE as default

COPY ansible /ansible

RUN <<EOF
	dnf install -y python3 python3-pip

	python3 -m pip install --upgrade pip
	python3 -m pip install --upgrade ansible

    ansible-playbook ansible/ci_docker.yaml

	dnf clean all
	rm -rf /var/cache/dnf/
EOF

CMD ["/bin/bash"]
