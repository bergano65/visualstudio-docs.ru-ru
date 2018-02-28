---
title: "Функция SccGetVersion | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2aef7ed21124c2e3555442819461f1989388ab22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
|WORD|Описание:|  
|----------|-----------------|  
|HIWORD|Основной номер версии|  
|LOWORD|Дополнительный номер версии|  
  
## <a name="remarks"></a>Примечания  
 Например если подключаемый модуль системы управления версиями поддерживает версии 1.3 API-интерфейса подключаемого модуля управления источника, эта функция возвращала 0x0103.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)