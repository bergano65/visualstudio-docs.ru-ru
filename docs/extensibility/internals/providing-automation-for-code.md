---
title: Предоставление автоматизации для кода | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f9dbb7a8ddad39f01f5b29443168eebe12a2da8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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