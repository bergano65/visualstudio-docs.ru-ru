---
title: "IDiaStackWalker | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalker - интерфейс"
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackWalker
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Предоставляет методы, чтобы выполнить проверку стека, используя информацию в файле pdb.  
  
## Синтаксис  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDiaStackWalker`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Извлекает перечислитель кадра стека для платформ x86.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Извлекает перечислитель кадра стека для указанного типа платформы.|  
  
## Заметки  
 Этот интерфейс используется для получения списка кадров стека для загруженного модуля.  Каждый из методов передаются [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) объект \(реализованный клиентским приложением\), который предоставляет необходимые сведения для создания списка кадров стека.  
  
## Замечания для вызывающих объектов  
 Этот интерфейс полученного вызовом метода `CoCreateInstance` метод с идентификатором класса  `CLSID_DiaStackWalker` и идентификатор интерфейса  `IID_IDiaStackWalker`.  Примере показано, как получить этот интерфейс.  
  
## Пример  
 В этом примере показано, как получить `IDiaStackWalker` интерфейс.  
  
```cpp#  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## Требования  
 Заголовок: Dia2.h  
  
 Библиотеки: diaguids.lib  
  
 Библиотеки DLL: msdia80.dll  
  
## См. также  
 [Интерфейсы \(SDK для доступа к интерфейсу отладки\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)