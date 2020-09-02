---
title: Перечислитель кода состояния файла | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1b6e74caa9eedd42e25339d62f5837ccfe82d001
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204375"
---
# <a name="file-status-code-enumerator"></a>Перечислитель кода состояния файла
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`SccStatus`Перечислитель содержит именованные постоянные значения, которые определяют состояние файла в системе управления версиями. Это перечисление используется [скккуеринфо](../extensibility/sccqueryinfo-function.md) и `POPLISTFUNC` функцией обратного вызова (Дополнительные сведения см. в разделе [поплистфунк](../extensibility/poplistfunc.md) ).  
  
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
 Не удалось получить состояние; не полагайтесь на нее.  
  
 SCC_STATUS_NOTCONTROLLED  
 Файл не находится в системе управления версиями.  
  
 SCC_STATUS_CONTROLLED  
 Файл находится в системе управления версиями.  
  
 SCC_STATUS_CHECKEDOUT  
 Извлечен текущим пользователем на локальном диске.  
  
 SCC_STATUS_OUTOTHER  
 Файл извлечен другим пользователем.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 Файл извлечен в монопольном режиме.  
  
 SCC_STATUS_OUTMULTIPLE  
 Файл извлечен более чем одним пользователем.  
  
 SCC_STATUS_OUTOFDATE  
 Файл не является самым последним.  
  
 SCC_STATUS_DELETED  
 Файл был удален из проекта.  
  
 SCC_STATUS_LOCKED  
 Файл заблокирован; больше нет разрешенных версий.  
  
 SCC_STATUS_MERGED  
 Файл был объединен, но еще не исправлен или проверен.  
  
 SCC_STATUS_SHARED  
 Файл является общим для проектов.  
  
 SCC_STATUS_PINNED  
 Файл является общим для явной версии.  
  
 SCC_STATUS_MODIFIED  
 Файл был изменен, поврежден или нарушен.  
  
 SCC_STATUS_OUTBYUSER  
 Файл извлечен текущим пользователем.  
  
 SCC_STATUS_NOMERGE  
 Файл не может быть объединен с и не должен быть сохранен перед ПОЛУЧЕНИЕм.  
  
 SCC_STATUS_RESERVED_1  
 Зарезервировано для внутреннего использования.  
  
 SCC_STATUS_RESERVED_2  
 Зарезервировано для внутреннего использования.  
  
## <a name="see-also"></a>См. также:  
 [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)   
 [скккуеринфо](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)
