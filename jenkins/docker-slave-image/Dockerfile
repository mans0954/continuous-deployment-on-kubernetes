FROM jenkinsci/jnlp-slave
MAINTAINER Vic Iglesias <viglesias@google.com>

ENV CLOUDSDK_CORE_DISABLE_PROMPTS 1
ENV PATH /opt/google-cloud-sdk/bin:$PATH

USER root

RUN apt-get update -y
RUN apt-get install -y jq \
      libapparmor-dev \
      libseccomp-dev \
      make
RUN  apt-get install -y \
     apt-transport-https \
     ca-certificates \
     curl \
     gnupg2 \
     software-properties-common
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN  add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
RUN apt-get update -y
RUN apt-get install -y docker-ce
RUN curl https://sdk.cloud.google.com | bash && mv google-cloud-sdk /opt
RUN gcloud components install kubectl
