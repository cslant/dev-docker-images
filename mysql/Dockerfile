FROM mysql:8.0.35

LABEL maintainer="Tan Nguyen <tannp@cslant.com>"
LABEL authors="cslant"
LABEL description="MySQL image for CSlant development"

#####################################
# Set Timezone
#####################################
ARG TZ=Asia\Ho_Chi_Minh
ENV TZ ${TZ}
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone && chown -R mysql:root /var/lib/mysql/

COPY my.cnf /etc/mysql/conf.d/my.cnf

RUN chmod 0444 /etc/mysql/conf.d/my.cnf

CMD ["mysqld"]

EXPOSE 3306
