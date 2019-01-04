---
title: Перечислитель кода состояния каталога | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a8d6a541415e42e8d35dc4f3ab814c89cf939beb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927614"
---
# <a name="directory-status-code-enumerator"></a>Перечислитель кода состояния каталога
`SccDirStatus` Перечислитель содержит именованные константы, определяющие состояние каталога в системе управления версиями. Это перечисление используется с [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Это была введена в версии 1.2 API подключаемых модулей управления источника.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>Участники  
 SCC_DIRSTATUS_INVALID  
 Не удалось получить состояние; не следует полагаться на него.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 Каталог не существует в системе управления версиями.  
  
 SCC_DIRSTATUS_CONTROLLED  
 Каталог находится внутри системы управления версиями.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 Проект, соответствующий в этот каталог является пустым.  
  
## <a name="see-also"></a>См. также  
 [Подключаемых модулей системы управления версиями](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)