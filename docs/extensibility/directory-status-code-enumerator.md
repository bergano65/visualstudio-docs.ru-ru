---
title: "Перечислитель код состояния каталога | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a29b9453fa7fd36564fef2956c1d41cc7f29cf07
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="directory-status-code-enumerator"></a>Перечислитель код состояния каталога
`SccDirStatus` Перечислитель содержит именованные константы, определяющие состояние каталога в системе управления версиями. Это перечисление используется методом [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Это впервые появилась в версии 1.2 API подключаемых модулей управления источника.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>Участники  
 SCC_DIRSTATUS_INVALID  
 Не удалось получить состояние; не следует полагаться на него.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 Каталог не существует в системе управления версиями.  
  
 SCC_DIRSTATUS_CONTROLLED  
 Каталог находится в системе управления версиями.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 Проект, соответствующий в этот каталог пуст.  
  
## <a name="see-also"></a>См. также  
 [Подключаемые модули управления версиями](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)