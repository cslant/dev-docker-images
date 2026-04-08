FROM postgres:18-alpine
LABEL maintainer="Tan Nguyen <tannp@cslant.com>"
LABEL authors="cslant"
LABEL description="Postgres18 image for CSlant development"

#####################################
# Set Timezone
#####################################
ARG TZ=Asia\Ho_Chi_Minh
ENV TZ=${TZ}
RUN mkdir -p /var/lib/postgresql/data && \
    ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
    echo $TZ > /etc/timezone && \
    chown -R postgres:root /var/lib/postgresql/data

COPY pg.cnf /etc/postgresql/conf.d/pg.cnf

RUN chmod 0444 /etc/postgresql/conf.d/pg.cnf

CMD ["postgres"]

EXPOSE 5432
