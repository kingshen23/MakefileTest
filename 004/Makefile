#004 makefile 初步加入obj文件夹，但不理想
#
#
#
#
target=mkTest004
compile=cc
CFLAGS  = -g -Wall -O2
# makefile 主要是依赖关系，具体的指令可以查看gcc的手册
C_SRCS=$(foreach dir, src, $(wildcard $(dir)/*.c))
object=$(patsubst %.c, obj/%.o, $(C_SRCS))

INC_PATH    = -I inc
LIB_PATH    = -L lib
EXT_LIB     = -lmyA -lmyB

# 用于产生h文件的依赖关系 -MM指令
# gcc -MM main.c a.c b.c
.PHONY : all
all:$(target)	
	@echo "编译结束"
#	$(compile) -MM $(src)

# 展开:
# gcc -o mkTest000 main.o a.o b.o
$(target):$(object)
	$(compile) -o $(target) $(object) $(LIB_PATH) $(EXT_LIB) $(CFLAGS)
# 静态模式
# 自动化变量:"$<"=依赖目标集 "$@"= 目标集
# 展开:
# gcc -c a.c -o a.o
# gcc -c b.c -o b.o
# gcc -c main.c -o main.o
# $(object):可省略
$(object):obj/%.o:%.c
	$(compile) -c -o $@ $< $(INC_PATH) $(CFLAGS) 
	

#显示的高数makefile 是否与文件名重clean就是个伪目标
.PHONY: clean
clean:
	@echo "清除过程文件..."
	-rm $(target) $(object)


#必须用分号隔开置于同一行才起作用
exec:
	cd ../000;pwd