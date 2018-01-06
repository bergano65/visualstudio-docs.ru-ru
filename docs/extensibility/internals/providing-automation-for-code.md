---
title: "Предоставление автоматизации для кода | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e59f3826cbb2ed83510cd98209b4c83f9278397d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="providing-automation-for-code"></a>Предоставление автоматизации для кода
Создание модели автоматизации для кода не требуется. Пакет SDK для среды не предоставляет для этого образца. Для понимания модели кода, в разделе <xref:EnvDTE.CodeModel> объекта.  
  
 Для реализации модели кода, необходимо реализовать все интерфейсы, которые определяются структуры внутренних данных. Объект, который должен быть производным от `IDispatch` класса.  
  
 Объекты, которые расширяют возможности, <xref:EnvDTE.CodeModel> и <xref:EnvDTE.FileCodeModel>, доступны из <xref:EnvDTE.Project> объекта и выглядеть следующим образом:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Можно выбрать для реализации просто `CodeModel` или `FileCodeModel` интерфейса в объект возвращается из вашего `Project` и <xref:EnvDTE.ProjectItem> объектов. Предоставляет никакой функциональности из этого интерфейса, соответствующий вашей системе проектов.  
  
 Если вы хотите добавить компоненты, например методы или свойства, которые недоступны из стандартного `CodeModel` и `FileCodeModel` интерфейсы, создайте собственный интерфейс, наследуемый от стандартного. Убедитесь, что документ в системе проекта, чтобы конечные пользователи могут искать его. Возвращает стандартный интерфейс, но пользователь может вызвать `QueryInterface` метода или преобразование в интерфейс, если известно, что существует.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о модели автоматизации](../../extensibility/internals/automation-model-overview.md)