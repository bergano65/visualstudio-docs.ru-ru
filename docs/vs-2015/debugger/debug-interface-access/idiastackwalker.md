---
title: IDiaStackWalker | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a86cc22a26d553c0239beedb011b3ecb9d79f2f6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569063"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaStackWalker](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalker).  
  
Предоставляет методы, чтобы сделать стек стека, используя сведения в PDB-файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaStackWalker`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Извлекает перечислитель кадр стека для x86 платформ.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Извлекает перечислитель кадр стека для типа конкретную платформу.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс используется для получения списка кадров стека для загруженного модуля. Каждый из методов передается [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) object (реализовано клиентским приложением), который предоставляет сведения, необходимые для создания списка кадров стека.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Этот интерфейс получается путем вызова `CoCreateInstance` метод с идентификатором класса `CLSID_DiaStackWalker` и идентификатор интерфейса `IID_IDiaStackWalker`. В примере показано, как этот интерфейс получается.  
  
## <a name="example"></a>Пример  
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
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотеки DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)



