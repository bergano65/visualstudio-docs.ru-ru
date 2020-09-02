---
title: Функция Сккжетверсион | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4e548f1f2b82a97206cdf41174a8c1c7d61e885
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200050"
---
# <a name="sccgetversion-function"></a>Функция SccGetVersion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция возвращает номер версии API подключаемого модуля системы управления версиями, поддерживаемый подключаемым модулем системы управления версиями.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Параметры  
 Нет.  
  
## <a name="return-value"></a>Возвращаемое значение  
 `LONG`Тип данных, содержащий номер версии поддерживаемого интерфейса API подключаемого модуля системы управления версиями:  
  
|WORD|Описание|  
|----------|-----------------|  
|HIWORD|Основной номер версии|  
|ловорд|Дополнительный номер версии|  
  
## <a name="remarks"></a>Remarks  
 Например, если подключаемый модуль системы управления версиями поддерживает версию 1,3 API подключаемого модуля системы управления версиями, эта функция возвратит 0x0103.  
  
## <a name="see-also"></a>См. также:  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
