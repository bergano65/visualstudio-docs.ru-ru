---
title: "События пользовательской собственной кучи трассировки событий Windows | Документы Майкрософт"
ms.custom: 
ms.date: 02/24/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
caps.latest.revision: 8
author: BrianPeek
ms.author: brpeek
manager: ghogen
dev_langs:
- C++
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 795bf9746c4ae48ac04141a05ba56462ecb90482
ms.openlocfilehash: afc044be4d63b7a292a6d94e360366913bd28883
ms.contentlocale: ru-ru
ms.lasthandoff: 06/23/2017

---

# <a name="custom-native-etw-heap-events"></a>События пользовательской собственной кучи трассировки событий Windows

Visual Studio содержит разнообразные [средства профилирования и диагностики](https://docs.microsoft.com/en-us/visualstudio/profiling/profiling-tools), включая встроенный профилировщик памяти.  Этот профилировщик обрабатывает [события ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) от поставщика кучи и анализирует выделение и использование памяти.  По умолчанию это средство может анализировать только выделения из стандартной кучи Windows, а выделения вне собственной кучи не отображаются.

Во многих случаях может потребоваться использовать пользовательскую кучу и исключить издержки при распределении из стандартной кучи.  Например, можно использовать [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx), чтобы выделить большой объем памяти при запуске приложения или игры, а затем управлять собственными блоками в рамках этого списка.  В этом случае средство профилирования памяти будет видеть только первоначальное выделение, а не пользовательское управление, выполняемые в блоке памяти.  Но с помощью поставщика ETW пользовательской собственной кучи можно указать средству на выделение, осуществляемые вне стандартной кучи.

Например, в проекте, аналогичном следующему, где `MemoryPool` является пользовательской кучей, будет доступно только одно выделение в куче Windows.

```cpp
class Foo
{
public:
    int x, y;
};

...

// MemoryPool is a custom managed heap, which allocates 8192 bytes 
// on the standard Windows Heap named "Windows NT"
MemoryPool<Foo, 8192> mPool;

// the "allocate" method requests memory from the pool created above
// and is cast to an object of type Foo, shown above
Foo* pFoo1 = (Foo*)mPool.allocate();
Foo* pFoo2 = (Foo*)mPool.allocate();
Foo* pFoo3 = (Foo*)mPool.allocate();
```

Моментальный снимок из средства [Использование памяти](https://docs.microsoft.com/en-us/visualstudio/profiling/memory-usage) без отслеживания пользовательской кучи будет отображать только одно 8192-байтовое выделение и ни одного из пользовательских выделений, сделанных пулом.

![Выделение кучи Windows](~/profiling/media/heap-example-windows-heap.png)

Выполнив следующие действия, можно использовать это же средство для отслеживания использования памяти в пользовательской куче.

## <a name="how-to-use"></a>Использование

Эту библиотеку можно легко использовать в C и C++.

1. Включите заголовок для поставщика ETW пользовательской кучи:

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. Добавьте декоратор `__declspec(allocator)` к любой функции в диспетчере пользовательской кучи, которая вернет указатель на только что выделенную память кучи.  Это декоратора позволяет средству правильно определять возвращаемый тип памяти.  Пример:

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```
   
   > [!NOTE]
   > Этот декоратор сообщит компилятору, что данная функция представляет собой вызов распределителя.  В результате каждого вызова функции будет выводиться адрес места вызова, размер инструкции вызова и идентификатор типа нового объекта для нового символа `S_HEAPALLOCSITE`.  После выделения стека вызовов Windows выдаст событие ETW с этими сведениями.  Средство профилирования памяти просматривает стек вызовов, чтобы найти обратный адрес, соответствующий символу `S_HEAPALLOCSITE`. Сведения об ИД типа в символе используются для отображения типа среды выполнения для выделения.
   >
   > Это означает, что вызов, который имеет вид `(B*)(A*)MyMalloc(sizeof(B))`, будет отображаться в средстве как имеющий типа `B`, а не `void` или `A`.

1. Для C++ создайте объект `VSHeapTracker::CHeapTracker`, указав имя для кучи, которое будет отображаться в средстве профилирования.

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   Если вы работаете с C, используйте функцию `OpenHeapTracker`.  Эта функция возвращает дескриптор, который будет использоваться при вызове других функций отслеживания.
  
   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. При выделении памяти с помощью настраиваемой функции вызовите метод `AllocateEvent` (C++) или `VSHeapTrackerAllocateEvent` (C), передав указатель на память и ее размер, чтобы отслеживать выделение.

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   или

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > Не забудьте пометить пользовательскую функцию распределителя декоратором `__declspec(allocator)`, описанным выше.

1. При освобождении памяти с помощью настраиваемой функции вызовите метод `DeallocateEvent` (C++) или `VSHeapTracerDeallocateEvent` (C), передав указатель на память и ее размер, чтобы отслеживать выделение.

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   или

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. При перераспределении памяти с помощью настраиваемой функции вызовите метод `ReallocateEvent` (C++) или `VSHeapReallocateEvent` (C), передав указатель на новую память, размер выделения и указатель на старую память.

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   или

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. И, наконец, чтобы закрыть и очистить средство отслеживания пользовательской кучи в C++, используйте деструктор `CHeapTracker` вручную или с помощью стандартных правила области видимости либо используйте функцию `CloseHeapTracker` в C.

   ```cpp
   delete pHeapTracker;
   ```

   или

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="tracking-memory-usage"></a>Отслеживание использования памяти
При наличии этих вызовов для отслеживания использования пользовательской кучи теперь можно применять стандартное средство **Использование памяти** в Visual Studio.  Дополнительные сведения об использовании этого средства см. в документации по средству [Использование памяти](https://docs.microsoft.com/en-us/visualstudio/profiling/memory-usage). Убедитесь, что вы включили профилирование кучи с моментальными снимками, в противном случае использование пользовательской кучи отображаться не будет. 

![Включение профилирования кучи](~/profiling/media/heap-enable-heap.png)

Чтобы просмотреть отслеживание пользовательской кучи, воспользуйтесь раскрывающимся списком **Куча**, расположенным в правом верхнем углу окна **Моментальный снимок**, для смены представления с *Куча NT* на вашу собственную кучу.

![Выбор кучи](~/profiling/media/heap-example-custom-heap.png)

Используя приведенный выше пример кода с `MemoryPool` для создания объекта `VSHeapTracker::CHeapTracker` и собственным методом `allocate`, вызывающим метод `AllocateEvent`, теперь можно увидеть результат пользовательского выделения — 3 экземпляра общим размером 24 байта с типом `Foo`.

*Куча NT* по умолчанию выглядит так же, как и ранее, но к ней добавлен объект `CHeapTracker`.

![Куча NT со средством отслеживания](~/profiling/media/heap-example-windows-heap.png)

Как и для стандартной кучи Windows, это средство можно использовать для сравнения моментальных снимков и поиска утечек и повреждений в пользовательской куче, как описывается в основной документации по средству [Использование памяти](https://docs.microsoft.com/en-us/visualstudio/profiling/memory-usage).

> [!TIP]
> Visual Studio также содержит средство **Использование памяти** в наборе инструментов **Профилирование производительности**, который доступен при выборе пунктов **Отладка > Профилировщик производительности** или при нажатии сочетания клавиш **ALT+F2**.  Эта функция не поддерживает отслеживание кучи и не отображает пользовательскую кучу, как описано здесь.  Эта возможность доступна только в диалоговом окне **Средства диагностики**, которое можно открыть, последовательно выбрав **Отладка > Окна > Показать средства диагностики**, либо нажав сочетание клавиш **CTRL+ALT+F2**.

## <a name="see-also"></a>См. также
* [Средства профилирования](https://docs.microsoft.com/en-us/visualstudio/profiling/profiling-tools)
* [Использование памяти](https://docs.microsoft.com/en-us/visualstudio/profiling/memory-usage)

