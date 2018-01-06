---
title: "Обзор (доступа к интерфейсу отладки SDK) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cb13b9a77bcd34b22a7a82182a63440cb02a4e76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="overview-debug-interface-access-sdk"></a>Общие сведения (SDK для доступа к интерфейсу отладки)
Используйте пакет SDK для доступа к данным Microsoft отладки. Пакет SDK для доступа к интерфейсу отладки предоставляет набор API, который избавляет от необходимости переписать всякий раз, когда Майкрософт изменяет формат отладочной информации на базе COM. ПАКЕТ SDK для также позволяет считывать из набора select для предыдущих версий отладочной информации в PDB-файл и .dbg файлах, создаваемых [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 5.0 и более поздних версиях.  
  
 В пакет SDK для каждого интерфейса представляет различных COM-объекта, за исключением того, там, где не указано иное. Дополнительные интерфейсы и, таким образом, дополнительные объекты, созданные с помощью явных запросов, такие как [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) или [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), а не путем вызова `QueryInterface` на существующих указателей интерфейса.  
  
## <a name="see-also"></a>См. также  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)