---
title: Файл состояния кода перечислителя | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: b3415440c80fcaa88edbecee924a118f82a9dd99
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="file-status-code-enumerator"></a>Перечислитель код состояния файла
`SccStatus` Перечислитель содержит именованных констант, определяющих состояние файла в системе управления версиями. Это перечисление используется методом [SccQueryInfo](../extensibility/sccqueryinfo-function.md) и `POPLISTFUNC` функция обратного вызова (в разделе [POPLISTFUNC](../extensibility/poplistfunc.md) подробные сведения).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## <a name="members"></a>Участники  
 SCC_STATUS_INVALID  
 Не удалось получить состояние; не следует полагаться на него.  
  
 SCC_STATUS_NOTCONTROLLED  
 Файл не задействован в системе управления версиями.  
  
 SCC_STATUS_CONTROLLED  
 Файл находится в системе управления версиями.  
  
 SCC_STATUS_CHECKEDOUT  
 Извлечен текущим пользователем, на локальном диске.  
  
 SCC_STATUS_OUTOTHER  
 Файл извлечен другим пользователем.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 Файл монопольно извлеченных.  
  
 SCC_STATUS_OUTMULTIPLE  
 Файл извлечен более чем одним пользователем.  
  
 SCC_STATUS_OUTOFDATE  
 Файл не является последней.  
  
 SCC_STATUS_DELETED  
 Файл был удален из проекта.  
  
 SCC_STATUS_LOCKED  
 Файл заблокирован; Дополнительные версии не допускается.  
  
 SCC_STATUS_MERGED  
 Файл был слияние, но еще не фиксированной и проверен.  
  
 SCC_STATUS_SHARED  
 Файл используется совместно между проектами.  
  
 SCC_STATUS_PINNED  
 Файл будет доступно для явного версии.  
  
 SCC_STATUS_MODIFIED  
 Файл был изменен или разбить/нарушено.  
  
 SCC_STATUS_OUTBYUSER  
 Файл извлечен текущим пользователем.  
  
 SCC_STATUS_NOMERGE  
 Файл не может быть объединена с и нет необходимости сохранять перед GET.  
  
 SCC_STATUS_RESERVED_1  
 Зарезервировано для внутреннего использования.  
  
 SCC_STATUS_RESERVED_2  
 Зарезервировано для внутреннего использования.  
  
## <a name="see-also"></a>См. также  
 [Подключаемые модули управления версиями](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)