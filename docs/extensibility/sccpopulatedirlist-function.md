---
title: "Функция SccPopulateDirList | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4be6e63df26d3c4a9b6539276aa97f69e349b83c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="sccpopulatedirlist-function"></a>Функция SccPopulateDirList
Эта функция определяет, какие каталоги и (при необходимости) файлы хранятся в системе управления версиями, поскольку список каталогов для проверки.  
  
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
 [in] Функция обратного вызова вызывается для каждого путь к каталогу и (необязательно) имя файла в `lpDirPaths` (см. [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) подробные сведения).  
  
 pvCallerData  
 [in] Без изменений значение, передаваемое функции обратного вызова.  
  
 fOptions  
 [in] Сочетание значений, которые управляют обработкой каталогов (в разделе «Флаги PopulateDirList» [битовые флаги, используемые определенные команды](../extensibility/bitflags-used-by-specific-commands.md) возможные значения).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Успешно завершил операцию.|  
|SCC_E_UNKNOWNERROR|Произошла ошибка.|  
  
## <a name="remarks"></a>Примечания  
 Функции обратного вызова, передаются только те каталоги и (необязательно) имена файлов, которые действительно находятся в хранилище системы управления версиями.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Битовые флаги, используемые определенных команд](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Коды ошибок](../extensibility/error-codes.md)