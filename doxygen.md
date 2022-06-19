sudo apt install doxygen graphviz 
doxygen -g  生成 doxygen 配置文件 Doxyfile
vim Doxygen

BUILTIN_STL_SUPPORT    = YES
EXTRACT_ALL            = YES
EXTRACT_PRIVATE        = YES
EXTRACT_PRIV_VIRTUAL   = YES
EXTRACT_PACKAGE        = YES
EXTRACT_STATIC         = YES
EXTRACT_LOCAL_METHODS  = YES
CLASS_DIAGRAMS      = YES
HIDE_UNDOC_RELATIONS = NO
HAVE_DOT             = YES
CLASS_GRAPH          = YES
COLLABORATION_GRAPH  = YES
UML_LOOK             = YES
UML_LIMIT_NUM_FIELDS = 50
TEMPLATE_RELATIONS   = YES
DOT_GRAPH_MAX_NODES  = 100
MAX_DOT_GRAPH_DEPTH  = 0
DOT_TRANSPARENT      = YES
INTERACTIVE_SVG        = YES
DOT_IMAGE_FORMAT = svg

doxygen Doxygen
然后去 html 文件夹
ls *.svg -Slrh

sudo apt install  texlive-full
cd latex
make   生成pdf
