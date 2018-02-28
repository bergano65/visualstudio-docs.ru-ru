---
title: "IActiveScript::AddTypeLib | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2be7cf033b4b5dd4d99b19a3b71ed53e32af855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Добавляет библиотеку типов в пространство имен для скрипта. Это похоже на `#include` директив в C/C++. Он позволяет набор стандартных элементов, таких как определения классов `typedefs`и именованных констант для добавления среды выполнения, которые доступны для скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidTypeLib`  
 [in] Код CLSID библиотеки типов для добавления.  
  
 `dwMaj`  
 [in] Основной номер версии.  
  
 `dwMin`  
 [in] Дополнительный номер версии.  
  
 `dwFlags`  
 [in] Флаги для параметра. Могут быть следующими:  
  
|Значение|Значение|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|Библиотека типов описывает элемент управления ActiveX, используемого ведущим приложением.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Недопустимый аргумент.|  
|`E_UNEXPECTED`|Вызов не ожидалось (например, обработчик сценариев еще не загрузки или инициализации).|  
|`TYPE_E_CANTLOADLIBRARY`|Не удалось загрузить библиотеки указанного типа.|  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)