---
title: Функция SccGetVersion | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe071cb0c0de62f4e59785f829adfaacc992336
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023542"
---
# <a name="sccgetversion-function"></a>Функция SccGetVersion
Эта функция возвращает номер версии API подключаемых модулей управления источника, поддерживает подключаемый модуль системы управления версиями.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Параметры  
 Отсутствует.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `LONG` тип данных, который содержит номер версии поддерживаемых API подключаемых модулей управления источника:  
  
|WORD|Описание:|  
|----------|-----------------|  
|HIWORD|Основной номер версии|  
|LOWORD|Дополнительный номер версии|  
  
## <a name="remarks"></a>Примечания  
 Например если подключаемый модуль системы управления версиями поддерживает версии 1.3 API подключаемых модулей управления источника, эта функция должна вернуть 0x0103.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)