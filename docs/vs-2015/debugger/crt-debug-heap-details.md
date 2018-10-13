---
title: Сведения о куче отладки CRT | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debug heap, accessing
- heap functions
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CrtMemDumpStatistics function
- debugging [C++], debug heap
- _CRT_BLOCK macro
- DBGINT.H file
- _CrtMemDumpAllObjectsSince function
- _crtBreakAlloc global variable
- _CrtMemState function
- _CLIENT_BLOCK macro
- _FREE_BLOCK block
- _CrtMemBlockHeader function
- heap state reporting functions
- _CRTDBG_ALLOC_MEM_DF macro
- _CrtSetBreakAlloc function
- memory blocks, allocation types on debug heap
- debugging [C++], CRT debug support
- debug heap, tracking heap allocation requests
- memory allocation, debug heap
- _NORMAL_BLOCK block
- crtBreakAlloc global variable
- _CrtDoForAllClientObjects function
- new operator, using debug heap from C++
- _CrtSetDumpClient function
- debugging [CRT], heap-related problems
- debug heap, solving memory allocation problems
- _CrtMemCheckpoint function
- debug builds, linking to debug heap
- _IGNORE_BLOCK block
- _crtDbgFlag function
- client blocks, specifying subtypes
- memory leaks, tracking
- _CrtSetDbgFlag function
- nBlockUse method
- memory leaks, CRT debug library functions
- _CRTDBG_DELAY_FREE_MEM_DF macro
- allocation request numbers
- _CRTDBG_LEAK_CHECK_DF macro
- debug heap
- memory, debugging
- _CrtReportBlockType function
- _CrtDumpMemoryLeaks function
- _CrtCheckMemory function
- debug heap, CRT
- memory blocks, free
- _BLOCK_TYPE macro
- debug heap, memory blocks
- heap allocation, debug
- debugging memory leaks
- _BLOCK_SUBTYPE macro
- debug heap, using from C++
- _CrtMemDifference function
- heap allocation, tracking requests
- debugging [Visual Studio], debug heap
- delete operator, using debug heap from C++
- blocks, types of on the debug heap
- _CRTDBG_CHECK_CRT_DF macro
- debug heap, reporting functions
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a97054db575d1d92f2077efe46d89573fba02dfd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49297748"
---
# <a name="crt-debug-heap-details"></a>Сведения о куче отладки CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе представлен подробный обзор отладочной кучи CRT.  
  
##  <a name="BKMK_Contents"></a> Описание  
 [Поиск переполнений буфера с помощью отладочной кучи](#BKMK_Find_buffer_overruns_with_debug_heap)  
  
 [Типы блоков в отладочной куче](#BKMK_Types_of_blocks_on_the_debug_heap)  
  
 [Проверка целостности кучи и памяти утечек](#BKMK_Check_for_heap_integrity_and_memory_leaks)  
  
 [Настройка отладочной кучи](#BKMK_Configure_the_debug_heap)  
  
 [New, delete и _CLIENT_BLOCK в C++ отладочной кучи](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)  
  
 [Функции создания отчетов о состоянии кучи](#BKMK_Heap_State_Reporting_Functions)  
  
 [Отслеживание запросов выделения кучи](#BKMK_Track_Heap_Allocation_Requests)  
  
##  <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> Поиск переполнений буфера с помощью отладочной кучи  
 Две самые распространенные и трудноразрешимые проблемы, с которыми сталкиваются программисты, — это перезапись конца выделенного буфера и утечки памяти (невозможность освободить выделенную память, когда она уже не нужна). Отладочная куча предоставляет мощные средства для решения подобных проблем с памятью.  
  
 Отладочные версии функций кучи вызывают стандартные или базовые версии, используемые в окончательных построениях. Когда запрашивается блок памяти, диспетчер отладочной кучи выделяет из основной кучи блок памяти немного больше требуемого, и возвращает указатель на часть этого блока. Например, допустим, приложение содержит вызов: `malloc( 10 )`. В окончательном построении [malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) вызовет выделения основной куче, которая запросит выделение 10 байтов. В сборке отладки, однако `malloc` вызовет [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb), который затем следует вызвать выделение основной куче, которая запросит выделение 10 байтов и около 36 байтов дополнительную память. Все результирующие блоки памяти в отладочной куче подключаются к единому связанному списку, который упорядочивает их по времени выделения.  
  
 Дополнительная память, выделяемая программами выделения памяти в куче, используется для учета используемых системных ресурсов, для указателей, связывающих отладочные блоки памяти вместе, и для небольших буферов с обеих сторон данных для перехватывания перезаписи выделенной области.  
  
 На текущий момент структура заголовка блока, используемая для хранения данных учета использованных системных ресурсов отладочной кучи, объявляется в файле заголовка DBGINT.H.  
  
```  
typedef struct _CrtMemBlockHeader  
{  
// Pointer to the block allocated just before this one:  
    struct _CrtMemBlockHeader *pBlockHeaderNext;  
// Pointer to the block allocated just after this one:  
    struct _CrtMemBlockHeader *pBlockHeaderPrev;  
    char *szFileName;    // File name  
    int nLine;           // Line number  
    size_t nDataSize;    // Size of user block  
    int nBlockUse;       // Type of block  
    long lRequest;       // Allocation number  
// Buffer just before (lower than) the user's memory:  
    unsigned char gap[nNoMansLandSize];  
} _CrtMemBlockHeader;  
  
/* In an actual memory block in the debug heap,  
 * this structure is followed by:  
 *   unsigned char data[nDataSize];  
 *   unsigned char anotherGap[nNoMansLandSize];  
 */  
```  
  
 `NoMansLand` Буферы с обеих сторон области пользовательских данных блока в настоящее время размер 4 байта и они заполняются фиксированным значением байта используемые в куче, чтобы убедиться, что конец блока памяти пользователя не были перезаписаны. Новые блоки памяти отладочная куча тоже заполняет фиксированными значениями. Если хранить освобожденные блоки в связанном списке отладочной кучи (как объясняется ниже), эти блоки также будут заполняться фиксированным значением. В данный момент используются следующие действительные значения байтов:  
  
 NoMansLand (0xFD)  
 Буферы "NoMansLand" по обеим сторонам участка памяти, используемой приложением, заполняются значением 0xFD.  
  
 Освобожденные блоки (0xDD)  
 Освобожденные блоки в связанном списке отладочной кучи хранятся как неиспользуемые блоки и, если флаг `_CRTDBG_DELAY_FREE_MEM_DF` установлен, они заполняются значением 0xDD.  
  
 Новые объекты (0xCD)  
 Новые объекты при выделении памяти заполняются значением 0xCD.  
  
 ![К началу страницы](../debugger/media/pcs-backtotop.png "PCS_BackToTop")  
  
 ![К началу](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Содержание](#BKMK_Contents)  
  
##  <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> Типы блоков в отладочной куче  
 Каждому блоку памяти в отладочной куче присвоен один из пяти типов выделений памяти. Эти типы отслеживаются и по-разному фиксируются в отчетах в зависимости от целей: обнаружение утечки памяти или отчет о состоянии. Тип блока можно задать, выделив его с помощью непосредственного вызова одной из функций выделения отладочной кучи, такие как [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb). Пять типов блоков памяти в отладочной куче (в **nBlockUse** членом **_CrtMemBlockHeader** структуры), следующим образом:  
  
 **_NORMAL_BLOCK**  
 Вызов [malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) или [calloc](http://msdn.microsoft.com/library/17bb79a1-98cf-4096-90cb-1f9365cd6829) создает Обычный блок. Если планируется использование только обычных блоков и не требуются клиентские, можно определить [_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b), что приводит все выделение кучи вызывает должны быть сопоставлены с их отладочные эквиваленты в отладочном построении. Такой подход позволяет хранить сведения об имени файла и номере строки для каждого выделения в заголовке соответствующего блока.  
  
 `_CRT_BLOCK`  
 Блоки памяти, выделенные для внутреннего использования несколькими функциями библиотеки CRT, помечаются как CRT-блоки и могут обрабатываться отдельно. В результате для обнаружения утечки и других операций эти блоки несущественны. Выделение памяти никогда не работает с блоками типа CRT (не выделяет, не перераспределяет и не освобождает).  
  
 `_CLIENT_BLOCK`  
 В целях отладки приложение может специально отслеживать данную группу выделений путем выделения их как блоков памяти этого типа, применяя явные вызовы функций отладочной кучи. MFC, например, выделяет все **CObjects** как клиентские блоки; другие приложения могут хранить другие объекты памяти в клиентских блоках. Можно также задавать подтипы клиентских блоков — для более глубокого контроля. Чтобы задать подтип клиентского блока, сдвиньте номер влево на 16 бит и примените для него операцию `OR` с `_CLIENT_BLOCK`. Пример:  
  
```  
#define MYSUBTYPE 4  
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));  
```  
  
 Функции клиента-ловушка для дампа объекта, хранящегося в клиентских блоках могут быть установлены с помощью [_CrtSetDumpClient](http://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033)и потом вызываться всякий раз, когда отладочной функцией создается дамп клиентского блока. Кроме того [_CrtDoForAllClientObjects](http://msdn.microsoft.com/library/d0fdb835-3cdc-45f1-9a21-54208e8df248) может использоваться для вызова данной функции, предоставляемой приложением для каждого клиентского блока в отладочной куче.  
  
 **_FREE_BLOCK**  
 Обычно это блоки, которые освобождаются и удаляются из списка. Чтобы удостовериться, что в освобожденную память не продолжается запись, или чтобы эмулировать условия нехватки памяти, можно выбрать хранение освобожденных блоков в связанном списке, помеченных как свободные и заполненных фиксированным значением байта (на данный момент 0xDD).  
  
 **_IGNORE_BLOCK**  
 Операции отладочной кучи можно на время отключить. В течение этого времени блоки памяти хранятся в списке, но помечаются как пропускаемые блоки.  
  
 Чтобы определить тип и подтип данного блока, используйте функцию [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) и макросы **_BLOCK_TYPE** и **_BLOCK_SUBTYPE**. Макросы определяются (в crtdbg.h) следующим образом:  
  
```  
#define _BLOCK_TYPE(block)          (block & 0xFFFF)  
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)  
```  
  
 ![К началу](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Содержание](#BKMK_Contents)  
  
##  <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> Проверка целостности кучи и памяти утечек  
 Из кода могут быть доступны многие возможности отладочной кучи. В следующих разделах описываются эти возможности и способы их использования.  
  
 `_CrtCheckMemory`  
 Можно использовать вызов [_CrtCheckMemory](http://msdn.microsoft.com/library/457cc72e-60fd-4177-ab5c-6ae26a420765), например, для проверки целостности кучи в любой момент. Эта функция проверяет каждый блок памяти в куче, оценивает допустимость данных его заголовка, а также удостоверяется, что буферы не были изменены.  
  
 `_CrtSetDbgFlag`  
 Вы можно контролировать, как отладочная куча отслеживает выделения, с помощью внутреннего флага [_crtDbgFlag](http://msdn.microsoft.com/library/9e7adb47-8ab9-4e19-81d5-e2f237979973), который может читать и устанавливать [_CrtSetDbgFlag](http://msdn.microsoft.com/library/b5657ffb-6178-4cbf-9886-1af904ede94c) функции. Изменяя этот флаг, можно указать отладочной куче по завершении программы проверять память на утечки и формировать отчет при их обнаружении. Аналогично можно задать, чтобы освобожденные блоки не удалялись из связанного списка — для эмуляции условий нехватки памяти. Когда куча проверена, эти освобожденные блоки проверяются на целостность, чтобы убедиться, что они не были повреждены.  
  
 **_CrtDbgFlag** флаг содержит следующие битовые поля:  
  
|Битовое поле|Значение по умолчанию<br /><br /> value|Описание|  
|---------------|-----------------------|-----------------|  
|**_CRTDBG_ALLOC_MEM_DF**|включить|Включает отладочное выделение. Если этот бит отключен, выделения остаются скрепленными вместе, но типы их блоков — **_IGNORE_BLOCK**.|  
|**_CRTDBG_DELAY_FREE_MEM_DF**|Off|Препятствует действительному освобождению памяти, как при эмуляции условий нехватки памяти. Если этот бит включен, освобожденные блоки хранятся в связанном списке отладочной кучи, но помечаются как **_FREE_BLOCK** и заполняется значением байтов.|  
|**_CRTDBG_CHECK_ALWAYS_DF**|Off|Вызывает **_CrtCheckMemory** которая должна вызываться при каждом выделении и освобождении. Это замедляет выполнение, но позволяет быстро перехватывать ошибки.|  
|**_CRTDBG_CHECK_CRT_DF**|Off|Указывает, что блоки, помеченные как **_CRT_BLOCK** должны быть включены в операции обнаружения утечки и сравнения состояний. Если этот бит выключен, память, используемая внутренне библиотекой CRT, во время таких операций не обрабатывается.|  
|**_CRTDBG_LEAK_CHECK_DF**|Off|Диагностирование утечек выполняемых при выходе из программы путем вызова **_CrtDumpMemoryLeaks**. Если при попытке приложения освободить всю выделенную память происходит сбой, создается отчет об ошибке.|  
  
 ![К началу](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Содержание](#BKMK_Contents)  
  
##  <a name="BKMK_Configure_the_debug_heap"></a> Настройка отладочной кучи  
 Все функции кучи, такие как `malloc`, `free`, `calloc`, `realloc`, `new` и `delete`, разрешают своим отладочным эквивалентам действовать в отладочной куче. Когда освобождается блок памяти, отладочная куча автоматически проверяет целостность буферов по обеим сторонам выделенной области и выдает отчет об ошибке в случае их перезаписи.  
  
 **Использование отладочной кучи**  
  
-   Свяжите отладочное построение приложения с отладочной версией библиотеки CRT.  
  
 **Чтобы изменить один или несколько битовых полей флага _crtDbgFlag и создание нового состояния флага**  
  
1.  Вызовите `_CrtSetDbgFlag` с параметром `newFlag`, равным `_CRTDBG_REPORT_FLAG` (чтобы получить текущее состояние `_crtDbgFlag`), и сохраните возвращенное значение во временной переменной.  
  
2.  Включите любые биты, применив `OR`- ing (побитовое &#124; символ) временной переменной и соответствующей битовой маски (представленной в коде приложения константой манифеста).  
  
3.  Отключите остальные биты, применив побитовую операцию `AND` (символ амперсанда "&") для переменной и соответствующей битовой маски, инвертированной с помощью `NOT` (символ тильды "~").  
  
4.  Вызовите `_CrtSetDbgFlag` с параметром `newFlag` со значением, сохраненным в этой временной переменной, чтобы создать новое состояние для `_crtDbgFlag`.  
  
 Например, следующие строки кода включают автоматическое обнаружение утечек памяти и отключают проверку блоков типа `_CRT_BLOCK`:  
  
```  
// Get current flag  
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );  
  
// Turn on leak-checking bit.  
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;  
  
// Turn off CRT block checking bit.  
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;  
  
// Set flag to the new value.  
_CrtSetDbgFlag( tmpFlag );  
```  
  
 ![К началу](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Содержание](#BKMK_Contents)  
  
##  <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> New, delete и _CLIENT_BLOCK в C++ отладочной кучи  
 Отладочные версии библиотеки времени выполнения C содержат отладочные версии операторов C++ `new` и `delete`. При использовании типа выделения `_CLIENT_BLOCK` необходимо либо непосредственно вызвать отладочную версию оператора `new`, либо создать макросы, заменяющие оператор `new` в режиме отладки, как показано в следующем примере.  
  
```  
/* MyDbgNew.h  
 Defines global operator new to allocate from  
 client blocks  
*/  
  
#ifdef _DEBUG  
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)  
#else  
   #define DEBUG_CLIENTBLOCK  
#endif // _DEBUG  
  
/* MyApp.cpp  
        Use a default workspace for a Console Application to  
 *      build a Debug version of this code  
*/  
  
#include "crtdbg.h"  
#include "mydbgnew.h"  
  
#ifdef _DEBUG  
#define new DEBUG_CLIENTBLOCK  
#endif  
  
int main( )   {  
    char *p1;  
    p1 =  new char[40];  
    _CrtMemDumpAllObjectsSince( NULL );  
}  
```  
  
 Отладочная версия оператора `delete` работает со всеми типами блоков и не требует изменений в программе при компиляции версии выпуска.  
  
 ![К началу](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Содержание](#BKMK_Contents)  
  
##  <a name="BKMK_Heap_State_Reporting_Functions"></a> Функции создания отчетов о состоянии кучи  
 **_CrtMemState**  
  
 Чтобы сохранить снимок состояния кучи на текущий момент, используется структура _CrtMemState, определенная в CRTDBG.H:  
  
```  
typedef struct _CrtMemState  
{  
    // Pointer to the most recently allocated block:  
    struct _CrtMemBlockHeader * pBlockHeader;  
    // A counter for each of the 5 types of block:  
    size_t lCounts[_MAX_BLOCKS];  
    // Total bytes allocated in each block type:  
    size_t lSizes[_MAX_BLOCKS];  
    // The most bytes allocated at a time up to now:  
    size_t lHighWaterCount;  
    // The total bytes allocated at present:  
    size_t lTotalCount;  
} _CrtMemState;  
```  
  
 Эта структура сохраняет указатель на первый (выделенный последним) блок в связанном списке отладочной кучи. Затем в двух массивах она записывает, сколько блоков памяти каждого типа (_NORMAL_BLOCK, `_CLIENT_BLOCK`, _FREE_BLOCK и т. д.) имеется в списке, а также количество байтов, выделенных в блоке каждого типа. И наконец она записывает наибольшее количество байтов, выделенных в куче до настоящего времени, а также количество байтов, выделенных в данный момент.  
  
 **Другие функции отчетов CRT**  
  
 Эти функции отчитываются о состоянии и содержимом кучи, использование этих сведений помогает обнаружить утечки памяти и решить другие подобные проблемы.  
  
|Функция|Описание|  
|--------------|-----------------|  
|[_CrtMemCheckpoint](http://msdn.microsoft.com/library/f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc)|Сохраняет снимок кучи в **_CrtMemState** структуру, предоставляемую приложением.|  
|[_CrtMemDifference](http://msdn.microsoft.com/library/0f327278-b551-482f-958b-76941f796ba4)|Сравнивает две структуры состояния памяти, сохраняет в третьей структуре различие между ними и возвращает значение TRUE при нахождении различий.|  
|[_CrtMemDumpStatistics](http://msdn.microsoft.com/library/27b9d731-3184-4a2d-b9a7-6566ab28a9fe)|Выводит заданный **_CrtMemState** структуры. Структура может содержать снимок состояния отладочной кучи на данный момент или различие между двумя состояниями.|  
|[_CrtMemDumpAllObjectsSince](http://msdn.microsoft.com/library/c48a447a-e6bb-475c-9271-a3021182a0dc)|Выводит сведения обо всех объектах, выделенных с момента получения данного снимка кучи или с начала выполнения. Каждый раз при **_CLIENT_BLOCK** блока, вызывается функция-ловушка приложения, если она была установлена с помощью **_CrtSetDumpClient**.|  
|[_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c)|Определяет, не произошла ли утечка памяти с начала выполнения программы, и, если произошла, выводит все выделенные объекты. Каждый раз **_CrtDumpMemoryLeaks** дампов **_CLIENT_BLOCK** блока, вызывается функция-ловушка приложения, если она была установлена с помощью **_CrtSetDumpClient**.|  
  
 ![К началу](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Содержание](#BKMK_Contents)  
  
##  <a name="BKMK_Track_Heap_Allocation_Requests"></a> Отслеживание запросов выделения кучи  
 Хотя точное указание имени исходного файла и номера строки, на которой стоит утверждение или выполняется макрос, часто очень полезно для выявления причины проблемы, этого не всегда достаточно для функций выделения кучи. Поскольку макросы могут вставляться в разные места логического дерева приложения, выделение часто скрыто в специальной программе из библиотеки DLL, которая тоже может вызываться из разных мест и в разное время. И поэтому вопрос обычно не в том, какая строка кода осуществила некорректное выделение, а в том, которое из тысяч выделений, сделанных этой строкой, было некорректным и почему.  
  
 **Уникальные номера запросов выделения и _crtBreakAlloc**  
  
 Наиболее простой способ идентифицировать запрос на указанное выделение кучи, ставшее некорректным, — воспользоваться преимуществом уникального номера запроса выделения, связанного с каждым блоком в отладочной куче. Когда данные о блоке помещены в отчет одной из функций дампа, этот номер запроса выделения заключается в фигурные скобки (например, "{36}«).  
  
 Узнав номер запроса выделения некорректно выделенного блока, вы можете передать в [_CrtSetBreakAlloc](http://msdn.microsoft.com/library/33bfc6af-a9ea-405b-a29f-1c2d4d9880a1) создать точку останова. Перед выделением блока выполнение прервется, и можно вернуться и определить, какая процедура отвечает за плохой вызов. Чтобы избежать перекомпиляции, можно выполнить то же самое в отладчике, задав **_crtBreakAlloc** номер запроса выделения, которые вас интересуют.  
  
 **Создание отладочных версий процедур выделения**  
  
 Несколько более сложный подход — создание отладочных версий собственных процедур выделения, сопоставимых с **_dbg** версиях [функции выделения кучи](../debugger/debug-versions-of-heap-allocation-functions.md). Можно передать аргументы исходного файла и номера строки базовым процедурам выделения кучи и сразу же увидеть, где возникло проблемное выделение.  
  
 Например, допустим, что приложение содержит обычную процедуру, наподобие следующей:  
  
```  
int addNewRecord(struct RecStruct * prevRecord,  
                 int recType, int recAccess)  
{  
    // ...code omitted through actual allocation...   
    if ((newRec = malloc(recSize)) == NULL)  
    // ... rest of routine omitted too ...   
}  
```  
  
 В файле заголовка можно добавить следующий код:  
  
```  
#ifdef _DEBUG  
#define  addNewRecord(p, t, a) \  
            addNewRecord(p, t, a, __FILE__, __LINE__)  
#endif  
```  
  
 Затем можно изменить выделение в процедуре создания записи следующим образом:  
  
```  
int addNewRecord(struct RecStruct *prevRecord,  
                int recType, int recAccess  
#ifdef _DEBUG  
               , const char *srcFile, int srcLine  
#endif  
    )  
{  
    /* ... code omitted through actual allocation ... */  
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,  
            srcFile, scrLine)) == NULL)  
    /* ... rest of routine omitted too ... */  
}  
```  
  
 Теперь имя исходного файла и номер строки, где вызывалась `addNewRecord`, будут сохранены в каждом выделенном в отладочной куче блоке и помещены в отчет при проверке этого блока.  
  
 ![К началу](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Содержание](#BKMK_Contents)  
  
## <a name="see-also"></a>См. также  
 [Отладка машинного кода](../debugger/debugging-native-code.md)



