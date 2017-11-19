---
title: "Функция SccDirQueryInfo | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccDirQueryInfo
helpviewer_keywords: SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aa1bc3624c8d03cfc484aaace906c2660c3a790e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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