---
title: Функция SccBackgroundGet | Документация Майкрософт
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
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 162bbc427b48ee10ea3a0b88837cf012f1c3fd07
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557903"
---
# <a name="sccbackgroundget-function"></a>Функция SccBackgroundGet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [функция SccBackgroundGet](https://docs.microsoft.com/visualstudio/extensibility/sccbackgroundget-function).  
  
Эта функция извлекает из системы управления версиями каждого из указанных файлов без участия пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 nFiles  
 [in] Число файлов, указанных в `lpFileNames` массива.  
  
 lpFileNames  
 [in, out] Массив имен файлов, которые требуется получить.  
  
> [!NOTE]
>  Имена должны быть полное локальные имена файлов.  
  
 dwFlags  
 [in] Команда флаги (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 dwBackgroundOperationID  
 [in] Уникальное значение, связанное с данной операцией.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Операция успешно завершена.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Получение фона уже выполняется (подключаемый модуль системы управления версиями вы получите это только в том случае, если он не поддерживает одновременное пакетных операций).|  
|SCC_I_OPERATIONCANCELED|Операция была отменена, прежде чем завершить.|  
  
## <a name="remarks"></a>Примечания  
 Эта функция всегда вызывается в потоке, отличном от того, в который загружен модуль управления версиями. Эта функция не должен возвращать до его завершения; Тем не менее он может вызываться несколько раз с нескольких списков файлов, для всех, в то же время.  
  
 Использование `dwFlags` аргумент совпадает со значением [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)

