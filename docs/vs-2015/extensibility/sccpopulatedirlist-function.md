---
title: Функция Сккпопулатедирлист | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6078f0fd90855c432b333fd5967367460d0a364e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200023"
---
# <a name="sccpopulatedirlist-function"></a>Функция SccPopulateDirList
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция определяет, какие каталоги и (при необходимости) файлы хранятся в системе управления версиями с учетом списка каталогов для проверки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccPopulateDirList(  
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
 окне Указатель контекста для подключаемого модуля системы управления версиями.  
  
 ндирс  
 окне Число путей к каталогу в `lpDirPaths` массиве.  
  
 лпдирпасс  
 окне Массив путей к каталогу для проверки.  
  
 пфнпопулате  
 окне Функция обратного вызова для вызова для каждого пути к каталогу и (при необходимости) имени файла в `lpDirPaths` (см. [попдирлистфунк](../extensibility/popdirlistfunc.md) для получения дополнительных сведений).  
  
 пвкаллердата  
 окне Значение, которое должно быть передано в функцию обратного вызова без изменений.  
  
 фоптионс  
 окне Сочетание значений, управляющих обработкой каталогов (см. раздел "Популатедирлист Flags" в [битфлагс, используемый конкретными командами](../extensibility/bitflags-used-by-specific-commands.md) для возможных значений).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Операция успешно завершена.|  
|SCC_E_UNKNOWNERROR|Произошла ошибка.|  
  
## <a name="remarks"></a>Remarks  
 Функция обратного вызова передается только этим каталогам и (необязательно) именам файлов, фактически находящиеся в репозитории системы управления версиями.  
  
## <a name="see-also"></a>См. также:  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)   
 [Битфлагс, используемые конкретными командами](../extensibility/bitflags-used-by-specific-commands.md)   
 [попдирлистфунк](../extensibility/popdirlistfunc.md)   
 [Код ошибки](../extensibility/error-codes.md)
