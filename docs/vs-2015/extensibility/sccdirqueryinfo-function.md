---
title: Функция Сккдиркуеринфо | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7334ddd1ce6c7f9feac63253246e55b65121e18b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842357"
---
# <a name="sccdirqueryinfo-function"></a>Функция SccDirQueryInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция проверяет список полных каталогов на предмет их текущего состояния.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 окне Структура контекста подключаемого модуля системы управления версиями.  
  
 ндирс  
 окне Количество каталогов, выбранных для запроса.  
  
 лпдирнамес  
 окне Массив полных путей к запрашиваемым каталогам.  
  
 лпстатус  
 [вход, выход] Структура массива для подключаемого модуля системы управления версиями, которая возвращает флаги состояния (Дополнительные сведения см. в разделе [код состояния каталога](../extensibility/directory-status-code-enumerator.md) ).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:  
  
|Значение|Description|  
|-----------|-----------------|  
|SCC_OK|Запрос выполнен успешно.|  
|SCC_E_OPNOTSUPPORTED|Система управления исходным кодом не поддерживает эту операцию.|  
|SCC_E_ACCESSFAILURE|Возникла проблема при доступе к системе управления версиями, возможно, из-за проблем с сетью или состязаниями. Рекомендуется повторить попытку.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Неконкретный сбой.|  
  
## <a name="remarks"></a>Remarks  
 Функция заполняет массив возврата битовой маской битов из `SCC_DIRSTATUS` семейства (см. [код состояния каталога](../extensibility/directory-status-code-enumerator.md)), по одной записи для каждого указанного каталога. Массив состояния выделяется вызывающим объектом.  
  
 Интегрированная среда разработки использует эту функцию перед переименованием каталога, чтобы проверить, находится ли каталог в системе управления версиями, выполнив запрос на наличие соответствующего проекта. Если каталог не находится в системе управления версиями, интегрированная среда разработки может предоставить пользователю соответствующее предупреждение.  
  
> [!NOTE]
> Если подключаемый модуль системы управления версиями не реализует одно или несколько значений состояния, нереализованные биты должны быть равны нулю.  
  
## <a name="see-also"></a>См. также:  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)   
 [Код состояния каталога](../extensibility/directory-status-code-enumerator.md)
