FROM icr.io/appc-dev/ace-server@sha256:a41f7501fe4025d2705bcabf1ad2ff523bcaf9ec263b98054501de1fc0cf5f62

ENV LICENSE=accept

COPY initial-config/ /home/aceuser/initial-config/

RUN . /opt/ibm/ace-12/server/bin/mqsiprofile


USER root

RUN /opt/ibm/ace-12/server/bin/mqsicreateworkdir /home/aceuser/ace-server-test

RUN chmod +x /usr/local/bin/*.sh
RUN  chmod -R ugo+rwx /home/aceuser

RUN . /opt/ibm/ace-12/server/bin/mqsiprofile
RUN /opt/ibm/ace-12/server/bin/ibmint deploy --input-bar-file /home/aceuser/initial-config/bars/TestDoru.bar --output-work-directory /home/aceuser/ace-server-test

RUN /opt/ibm/ace-12/server/bin/IntegrationServer --work-dir /home/aceuser/ace-server-test --test-project TestDoru_Test --start-msgflows false

USER aceuser
