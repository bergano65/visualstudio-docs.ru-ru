---
title: Перечислитель кода состояния файла | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cf7e39f91f6916f4d3ace7a9a303ea1c8e626ee9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954780"
---
# <a name="file-status-code-enumerator"></a>Перечислитель кода состояния файла
`SccStatus` Перечислитель содержит именованные константы, определяющие состояние файла в системе управления версиями. Это перечисление используется с [SccQueryInfo](../extensibility/sccqueryinfo-function.md) и `POPLISTFUNC` функцию обратного вызова (см. в разделе [POPLISTFUNC](../extensibility/poplistfunc.md) сведения).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## <a name="members"></a>Участники  
 SCC_STATUS_INVALID  
 Не удалось получить состояние; не следует полагаться на него.  
  
 SCC_STATUS_NOTCONTROLLED  
 Файл не существует в системе управления версиями.  
  
 SCC_STATUS_CONTROLLED  
 Файл находится в системе управления версиями.  
  
 SCC_STATUS_CHECKEDOUT  
 Извлечен текущим пользователем, на локальном диске.  
  
 SCC_STATUS_OUTOTHER  
 Файл извлечен другим пользователем.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 Файл извлечен монопольном режиме.  
  
 SCC_STATUS_OUTMULTIPLE  
 Файл извлечен более чем одним пользователем.  
  
 SCC_STATUS_OUTOFDATE  
 Файл не является последней.  
  
 SCC_STATUS_DELETED  
 Файл был удален из проекта.  
  
 SCC_STATUS_LOCKED  
 Файл заблокирован; Допускается наличие нескольких версий.  
  
 SCC_STATUS_MERGED  
 Файл были объединены, но еще не исправлены и проверены.  
  
 SCC_STATUS_SHARED  
 Файл распределяется между проектами.  
  
 SCC_STATUS_PINNED  
 Файл будет доступно для версии явно.  
  
 SCC_STATUS_MODIFIED  
 Файл был изменен или разбить/нарушено.  
  
 SCC_STATUS_OUTBYUSER  
 Файл извлечен текущим пользователем.  
  
 SCC_STATUS_NOMERGE  
 Файл никогда не могут быть объединены с и нет необходимости сохранять до запроса GET.  
  
 SCC_STATUS_RESERVED_1  
 Зарезервировано для внутреннего использования.  
  
 SCC_STATUS_RESERVED_2  
 Зарезервировано для внутреннего использования.  
  
## <a name="see-also"></a>См. также  
 [Подключаемых модулей системы управления версиями](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)