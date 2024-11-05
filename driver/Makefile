CONFIG_MODULE_SIG=n

modules:
	$(MAKE) ARCH=$(ARCH) CROSS_COMPILE=$(CROSS_COMPILE) -C $(KERNEL_SRC) M=$(shell pwd) modules

modules_install:
	$(MAKE) -C $(KERNEL_SRC) M=$(shell pwd) modules_install

strip:
	$(CROSS_COMPILE)strip ch343.ko --strip-unneeded

clean:
	rm -rf *.mk .tmp_versions Module.symvers *.mod.c *.o *.ko .*.cmd Module.markers modules.order *.a *.mod

load:
	insmod ch343.ko

unload:
	rmmod ch343

install:
	install -p -m 644 ch343.ko  $(MODDESTDIR)
	/sbin/depmod -a ${KVER}

uninstall:
	rm -f $(MODDESTDIR)/ch343.ko
	/sbin/depmod -a ${KVER}
