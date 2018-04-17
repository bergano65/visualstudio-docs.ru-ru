---
title: Исходных VSPackage конструктора элементов управления | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb741a7dc7423c27baed2cd79476239f4e41a170
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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