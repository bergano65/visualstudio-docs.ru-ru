---
title: IDiaStackWalker | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f50eede5ce9420e610c3859e5b54e41c9b88afd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Предоставляет методы, чтобы сделать стек стека, используя сведения в PDB-файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaStackWalker`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Извлекает перечислитель кадр стека для x86 платформы.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Извлекает перечислитель кадр стека для типа конкретную платформу.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс используется для получения списка кадров стека для загруженного модуля. Каждый из методов передается [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) object (реализованный в клиентском приложении), который предоставляет сведения, необходимые для создания списка кадров стека.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс можно получить, вызвав `CoCreateInstance` метод с кодом `CLSID_DiaStackWalker` и идентификатор интерфейса `IID_IDiaStackWalker`. В примере показано, как получить этот интерфейс.  
  
## <a name="example"></a>Пример  
 В этом примере показано, как получить `IDiaStackWalker` интерфейса.  
  
```C++  
  
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
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)