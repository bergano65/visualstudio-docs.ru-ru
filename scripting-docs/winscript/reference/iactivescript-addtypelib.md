---
title: 'IActiveScript:: Аддтипелиб | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 254a5133d42689020eaaae290a1016de4b848100
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575811"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Добавляет библиотеку типов в пространство имен для скрипта. Это похоже на директиву `#include` в C/C++. Он позволяет добавить в среду выполнения, доступную для скрипта, набор предопределенных элементов, таких как определения классов, `typedefs` и именованные константы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidTypeLib`  
 окне Идентификатор CLSID добавляемой библиотеки типов.  
  
 `dwMaj`  
 окне Основной номер версии.  
  
 `dwMin`  
 окне Дополнительный номер версии.  
  
 `dwFlags`  
 окне Флаги параметров. Может принимать следующие значение:  
  
|значения|Смысл|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|Библиотека типов описывает элемент управления ActiveX, используемый узлом.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Смысл|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Недопустимый аргумент.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не загружен или не инициализирован).|  
|`TYPE_E_CANTLOADLIBRARY`|Не удалось загрузить указанную библиотеку типов.|  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)