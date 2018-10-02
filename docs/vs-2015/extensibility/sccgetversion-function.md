---
title: Функция SccGetVersion | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2b5c5e5e6035d6ce0b81ba747efa3cea65ab2f97
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571411"
---
# <a name="sccgetversion-function"></a>Функция SccGetVersion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [функция SccGetVersion](https://docs.microsoft.com/visualstudio/extensibility/sccgetversion-function).  
  
Эта функция возвращает номер версии API подключаемых модулей управления источника, поддерживает подключаемый модуль системы управления версиями.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Например если подключаемый модуль системы управления версиями поддерживает версии 1.3 API подключаемых модулей управления источника, эта функция должна вернуть 0x0103.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)

