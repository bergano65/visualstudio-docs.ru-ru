---
title: Удаление данные системы управления версиями из. Proj и. SLN-файлы | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 695a4ccfc5da20bda25c78929488625c244959a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Удаление данные системы управления версиями из. Proj и. SLN-файлы
В версии 1.2 API подключаемых модулей управления источника SCC информация хранится в MSSCCPRJ. Файл SCC. Преимущество MSSCCPRJ. Файл SCC — что SCC сведения не источника - контролировать, как и в файлах ".proj" и .sln.  
  
## <a name="version-12-changes"></a>Изменения в версии 1.2  
 В исходном подключаемые модули управления, основанные на API подключаемых модулей управления исходной версии 1.1 сведения о системе управления версиями хранится в проект (".proj") и файлы решения (SLN). AuxPath задается расположение базы данных данные системы управления версиями и ProjName задается определенное место в базе данных. Это поведение может вызвать проблемы после ветвь, вилки или операций копирования, поскольку ProjName обычно будет недопустимым после любой из этих операций.  
  
 В API подключаемых модулей управления исходной версии 1.1, интегрированной среды разработки используется ~ SAK файлов для определения того, если подключаемый модуль поддерживается MSSCCPRJ. Метод SCC хранить данные системы управления версиями. API подключаемых модулей управления исходной версии 1.2 предоставляет новую возможность для обнаружения поддержка MSSCCPRJ. Файл SCC без использования ~ SAK файла. Дополнительные сведения см. в разделе [Устранение ~ SAK файлы](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>См. также  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)