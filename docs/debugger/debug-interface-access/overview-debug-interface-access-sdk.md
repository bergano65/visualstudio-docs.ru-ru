---
title: "Общие сведения (SDK для доступа к интерфейсу отладки) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "типы, определяемые пользователем"
  - "DBG-файлы"
  - "модули"
  - "интерфейсы [пакет SDK для доступа к интерфейсу отладки]"
  - "DBG-файлы"
  - "процедуры [пакет SDK для доступа к интерфейсу отладки]"
  - "исполняемые файлы"
  - "COM-объекты, в пакете SDK для доступа к интерфейсу отладки"
  - "компилируемые объекты"
  - "исполняемые образы"
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Общие сведения (SDK для доступа к интерфейсу отладки)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Используйте пакет SDK для доступа к интерфейсу отладки для доступа к microsoft отладочной информации.  Пакет SDK для доступа к интерфейсу отладки на основе модели COM предоставляет набор API, который исключает необходимость перезаписать код, когда Майкрософт изменяет формат данных отладки.  Пакет SDK для доступа к интерфейсу отладки также позволяет считывать из списка выберите набор предыдущих версий отладочные данные, pdb\-файлы, расположенную в файлах и .dbg созданных by [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] версии 5.0 и более поздней версии.  
  
 Каждый интерфейс в пакет SDK для доступа к интерфейсу отладки представляющий другое com\-объекта, за исключением случаев, когда указано в противном случае.  Дополнительные интерфейсы, и, таким образом, дополнительные объекты, созданные с помощью явных запросов, таких как [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) OR  [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), а не путем вызова  `QueryInterface` на существующих указателей интерфейса.  
  
## См. также  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)