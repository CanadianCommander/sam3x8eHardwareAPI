OBYCP = arm-none-eabi-objcopy
CC = arm-none-eabi-gcc
AR = arm-none-eabi-ar
LD = arm-none-eabi-ld
CFLAGS = --std=gnu11 -Ofast -mcpu=cortex-m3 -mthumb -fno-builtin --specs=nosys.specs --specs=nano.specs -ffreestanding
INCLD = -I ../3rdParty/ATMEL/ -I ../3rdParty/CMSIS/Include

OUTPUT_DIR = ../build
SRC_CC = contextSwitching/*.c UART/*.c Timers/*.c EEFC/*.c general/*.c PIO/*.c SPI/*.c

libsam3x8e.o : $(SRC_CC) $(OUTPUT_DIR)/.dirstamp
	$(CC) $(CFLAGS) -c $(SRC_CC) $(INCLD)
	mv ./*.o $(OUTPUT_DIR)
	rm -f ../build/$@
	$(LD) -r -o ../build/$@ ../build/*.o

$(OUTPUT_DIR)/.dirstamp:
	mkdir -p $(OUTPUT_DIR)
	touch $@

clean:
	rm ../build/libsam3x8e.o
	rm ../build/*.o
