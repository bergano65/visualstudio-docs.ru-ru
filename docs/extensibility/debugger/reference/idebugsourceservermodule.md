---
title: "IDebugSourceServerModule | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: caf51056af3172e5dd13c551bf61d9780e407b1e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Представляет сведения об исходном сервере, содержащихся в PDB-файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugSourceServerModule : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется подсистемой отладчика и использовать отладчик пользовательского интерфейса.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugSourceServerModule`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Извлекает массив сведений об исходном сервере.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll