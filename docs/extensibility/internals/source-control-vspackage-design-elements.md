---
title: "Исходных VSPackage конструктора элементов управления | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 234346aba360d70d3bbc673067d2634a5112d0f6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-vspackage-design-elements"></a>Исходные элементы VSPackage конструктора элемента управления
В этом разделе описаны структуры, VSPackage должен реализовать для глубокую интеграцию системы управления версиями. Он также содержит интерфейсы и службы, что система управления VSPackage могут реализовывать интерфейсы и службы системы управления версиями VSPackage можно использовать из других [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] компонентов для поддержки его источником управления модель и функциональные возможности.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Структура пакета VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Определяет структуру системы управления версиями пакета VSPackage.  
  
 [Связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Список исходных интерфейсов относящиеся к пакету управления и служб.  
  
 [Службы, предоставляемые](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Описывает службу управления версиями, предоставляемые элементом управления источником VSPackage.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Описывает, как создать пакет VSPackage, который не только предоставляет функций системы управления версиями, но можно использовать для настройки системы управления версиями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] система управления версиями пользовательского интерфейса.