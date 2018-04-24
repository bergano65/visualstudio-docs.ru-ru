---
title: Обзор (доступа к интерфейсу отладки SDK) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 807690edaf5626e3ec007a005717622592c14ce9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="overview-debug-interface-access-sdk"></a>Общие сведения (SDK для доступа к интерфейсу отладки)
Используйте пакет SDK для доступа к данным Microsoft отладки. Пакет SDK для доступа к интерфейсу отладки предоставляет набор API, который избавляет от необходимости переписать всякий раз, когда Майкрософт изменяет формат отладочной информации на базе COM. ПАКЕТ SDK для также позволяет считывать из набора select для предыдущих версий отладочной информации в PDB-файл и .dbg файлах, создаваемых [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 5.0 и более поздних версиях.  
  
 В пакет SDK для каждого интерфейса представляет различных COM-объекта, за исключением того, там, где не указано иное. Дополнительные интерфейсы и, таким образом, дополнительные объекты, созданные с помощью явных запросов, такие как [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) или [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), а не путем вызова `QueryInterface` на существующих указателей интерфейса.  
  
## <a name="see-also"></a>См. также  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)