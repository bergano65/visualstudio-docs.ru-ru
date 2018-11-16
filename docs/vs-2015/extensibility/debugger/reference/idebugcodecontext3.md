---
title: IDebugCodeContext3 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8cbbec576b4e7b17f1a87e9d60ed1857fb3157b5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733256"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Расширяет [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) интерфейс, чтобы обеспечить получение модулей и процессов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Реализуется отладчиков и потребляемых [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] отладочный пакет.  
  
## <a name="methods"></a>Методы  
 В дополнение к методам на `IDebugCodeContext2` интерфейс, этот интерфейс реализует следующие методы:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Извлекает ссылку на интерфейс модуля отладки.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Извлекает ссылку на интерфейс процесс отладки.|  
  
## <a name="remarks"></a>Примечания  
 Это дополнительный интерфейс, который обычно не должны быть реализованы.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

