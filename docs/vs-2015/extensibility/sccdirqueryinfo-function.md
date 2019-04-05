---
title: Функция SccDirQueryInfo | Документация Майкрософт
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
ms.openlocfilehash: b86ac7c701f96d467f0c059fc7e4b732699b1da5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979501"
---
# <a name="sccdirqueryinfo-function"></a>Функция SccDirQueryInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция проверяет список полных каталогов для их текущее состояние.  
  
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
 [in] Структура подключаемого модуля контекста исходного элемента управления.  
  
 nDirs  
 [in] Количество каталогов, выбранного для запроса.  
  
 lpDirNames  
 [in] Массив полных путей к каталогам должны запрашиваться.  
  
 lpStatus  
 [in, out] Структуры массива для подключаемого модуля для возврата флагов состояния системы управления версиями (см. в разделе [код состояния Directory](../extensibility/directory-status-code-enumerator.md) сведения).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Запрос успешно выполнен.|  
|SCC_E_OPNOTSUPPORTED|Системы управления исходным кодом не поддерживает эту операцию.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Обнаружена неспецифическая ошибка.|  
  
## <a name="remarks"></a>Примечания  
 Функция заполняет массиву возвращаемых значений с Битовая маска битов из `SCC_DIRSTATUS` семейства (см. в разделе [код состояния Directory](../extensibility/directory-status-code-enumerator.md)), одна запись для каждого каталога, заданного. Этот массив выделяется вызывающим объектом.  
  
 Интегрированная среда разработки использует эту функцию перед переименованием каталог для проверки, является ли каталог в системе управления версиями, запрашивая, имеет ли она соответствующего проекта. Если каталог не существует в системе управления версиями, интегрированной среды разработки можно указать правильное предупреждение для пользователя.  
  
> [!NOTE]
>  Если подключаемый модуль системы управления версиями решил не реализовывать один или несколько из указанных значений состояния, Нереализованная битов задается равным нулю.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Код состояния каталога](../extensibility/directory-status-code-enumerator.md)
