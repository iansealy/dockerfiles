FROM broadinstitute/gatk:4.5.0.0

WORKDIR /gatk
RUN perl -spi -e 's/use_async_io_write_samtools=true/use_async_io_write_samtools=false/g' gatk
