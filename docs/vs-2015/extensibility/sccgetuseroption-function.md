---
title: Функция Сккжетусероптион | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bd00a2b669b806b09a6ae221b2ba2e03f8d45ceb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200070"
---
# <a name="sccgetuseroption-function"></a>Функция SccGetUserOption
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция получает разнообразные параметры, относящиеся к пользователю.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 окне Указатель контекста для подключаемого модуля системы управления версиями.  
  
 ноптион  
 окне Параметр для извлечения (см. раздел Примечания для возможных параметров).  
  
 лпвал  
 заполняет Значение, связанное с параметром.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Параметр успешно получен.|  
|SCC_E_OPNOTSUPPORTED|Параметр не поддерживается.|  
|SCC_E_NONSPECIFICERROR|Произошла неизвестная ошибка.|  
  
## <a name="remarks"></a>Remarks  
 Эта команда поддерживает следующие параметры:  
  
|Параметр пользователя|Описание|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Определяет, хочет ли пользователь извлечь локальную версию файлов. `lpVal` назначается `SCC_USEROPT_COLV_YES` (пользователь хочет извлечь локальные файлы) или `SCC_USEROPT_COLV_NO` .|  
  
## <a name="see-also"></a>См. также:  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)   
 [Код ошибки](../extensibility/error-codes.md)
