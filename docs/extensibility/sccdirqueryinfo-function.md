---
title: Функция SccDirQueryInfo | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1de32b8502e40c953bd7080d64e56047e6bb5ce9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140372"
---
# <a name="sccdirqueryinfo-function"></a>Функция SccDirQueryInfo
Эта функция проверяет список полное каталогов для их текущего состояния.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Исходная структура подключаемого модуля контекста элемента управления.  
  
 nDirs  
 [in] Число выбранных должны запрашиваться каталоги.  
  
 lpDirNames  
 [in] Массив полное имя пути к папкам, должны запрашиваться.  
  
 lpStatus  
 [in, out] Структуры массива для системы управления версиями для возврата флаги состояния (см. [код состояния каталога](../extensibility/directory-status-code-enumerator.md) подробные сведения).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Запрос успешно.|  
|SCC_E_OPNOTSUPPORTED|Системы управления исходным кодом не поддерживает эту операцию.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Неспецифичную сбоя.|  
  
## <a name="remarks"></a>Примечания  
 Функция заполняет возвращаемого массива с битовой маской битов из `SCC_DIRSTATUS` семейство (см. [код состояния каталога](../extensibility/directory-status-code-enumerator.md)), одну запись для каждого заданного каталога. Этот массив, зарезервированный вызывающим.  
  
 Интегрированная среда разработки использует эту функцию перед переименованием каталог для проверки, является ли каталог в системе управления версиями, с помощью запроса, имеет ли соответствующий проект. Если каталог не существует в системе управления версиями, Интегрированной среде разработки можно указать правильную предупреждение для пользователя.  
  
> [!NOTE]
>  Если подключаемый модуль системы управления версиями решил не реализовывать один или несколько из указанных значений состояния, нереализованные bits должна равен нулю.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Код состояния каталога](../extensibility/directory-status-code-enumerator.md)