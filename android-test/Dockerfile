FROM ubuntu:12.04

MAINTAINER alexfu

RUN apt-get update -qq

# Dependencies to execute android
RUN apt-get install -y --no-install-recommends openjdk-7-jdk ia32-libs ia32-libs-multiarch git

# Main Android SDK
RUN apt-get install -y --no-install-recommends wget
RUN cd /opt && wget -q http://dl.google.com/android/android-sdk_r22.6-linux.tgz
RUN cd /opt && tar xzf android-sdk_r22.6-linux.tgz
RUN cd /opt && rm -f android-sdk_r22.6-linux.tgz

# Other tools and resources of Android SDK
ENV ANDROID_HOME /opt/android-sdk-linux
ENV PATH ${PATH}:${ANDROID_HOME}/tools:${ANDROID_HOME}/platform-tools
RUN echo y | android update sdk -a -u -f -t build-tools-19.1.0
RUN echo y | android update sdk -a -u -f -t android-19
RUN echo y | android update sdk -a -u -f -t addon-google_apis-google-19
RUN echo y | android update sdk -a -u -f -t extra-google-m2repository
RUN echo y | android update sdk -a -u -f -t extra-android-m2repository

# Cleaning
RUN apt-get clean
