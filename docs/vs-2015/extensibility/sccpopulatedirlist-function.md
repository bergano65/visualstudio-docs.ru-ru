---
title: Функция SccPopulateDirList | Документация Майкрософт
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
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 358512c94f46971cc91ef3ed065c83ba56e5ad16
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560320"
---
# <a name="sccpopulatedirlist-function"></a>Функция SccPopulateDirList
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [функция SccPopulateDirList](https://docs.microsoft.com/visualstudio/extensibility/sccpopulatedirlist-function).  
  
Эта функция определяет, какие каталоги и (при необходимости) файлы хранятся в системе управления версиями, при наличии списка каталогов для проверки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 nDirs  
 [in] Количество путей к каталогам в `lpDirPaths` массива.  
  
 lpDirPaths  
 [in] Массив путей к каталогам для проверки.  
  
 pfnPopulate  
 [in] Функция обратного вызова для вызова для каждого путь к каталогу и (необязательно) имя файла в `lpDirPaths` (см. в разделе [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) сведения).  
  
 pvCallerData  
 [in] Без изменений значение, передаваемое функции обратного вызова.  
  
 Возможности  
 [in] Сочетание значения, определяющие, как обрабатываются каталоги (см. в разделе «Флаги PopulateDirList» [битовые флаги, используемые конкретными командами](../extensibility/bitflags-used-by-specific-commands.md) возможные значения).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Операция успешно выполнена.|  
|SCC_E_UNKNOWNERROR|Произошла ошибка.|  
  
## <a name="remarks"></a>Примечания  
 Функции обратного вызова, передаются только те каталоги и (необязательно) имена файлов, которые фактически находятся в репозитории системы управления версиями.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Битовые флаги, используемые конкретными командами](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Коды ошибок](../extensibility/error-codes.md)

