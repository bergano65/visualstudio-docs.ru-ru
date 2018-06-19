---
title: Функция SccGetVersion | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70beb89f13d2f752f3adb0f25e2b370fa272171a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136449"
---
# <a name="sccgetversion-function"></a>Функция SccGetVersion
Эта функция возвращает номер версии API подключаемых модулей исходного элемента управления, поддерживаемых подключаемый модуль системы управления версиями.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Параметры  
 Отсутствует.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `LONG` тип данных, который содержит номер версии поддерживаемых API подключаемых модулей управления источника:  
  
|WORD|Описание|  
|----------|-----------------|  
|HIWORD|Основной номер версии|  
|LOWORD|Дополнительный номер версии|  
  
## <a name="remarks"></a>Примечания  
 Например если подключаемый модуль системы управления версиями поддерживает версии 1.3 API-интерфейса подключаемого модуля управления источника, эта функция возвращала 0x0103.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)