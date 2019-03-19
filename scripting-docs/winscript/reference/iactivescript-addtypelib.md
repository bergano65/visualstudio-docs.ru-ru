---
title: IActiveScript::AddTypeLib | Документация Майкрософт
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
ms.openlocfilehash: c4943d1305c2f25de4eec9e782949a66827de879
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144879"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Добавляет библиотеку типов в пространство имен для скрипта. Это похоже на `#include` директив в C/C++. Он позволяет набор стандартных пунктов, такие как определения классов, `typedefs`и именованные константы, добавляемых к среде выполнения, которые доступны для скрипта.  
  
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
 [in] CLSID библиотеки типов для добавления.  
  
 `dwMaj`  
 [in] Основной номер версии.  
  
 `dwMin`  
 [in] Дополнительный номер версии.  
  
 `dwFlags`  
 [in] Флаги параметров. Могут быть следующими:  
  
|Значение|Значение|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|Библиотека типов описывает элемент управления ActiveX, используемый узлом.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не была загрузки или инициализации).|  
|`TYPE_E_CANTLOADLIBRARY`|Не удалось загрузить указанной библиотеки типов.|  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)