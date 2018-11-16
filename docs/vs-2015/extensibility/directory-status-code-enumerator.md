---
title: Перечислитель кода состояния каталога | Документация Майкрософт
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
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a23bef10dda57d761ce7f07c3b87808b021830c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766661"
---
# <a name="directory-status-code-enumerator"></a>Перечислитель кода состояния каталога
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

