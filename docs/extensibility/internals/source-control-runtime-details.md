---
title: "Источник сведений среды выполнения элемента управления | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9647f1f399b0d6516fe6475e6245c6834a0ea2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-runtime-details"></a>Сведения об источнике управления среды выполнения
Проект добавляется в систему управления версиями, когда пользователь добавляет файл в проект в систему управления версиями, или с помощью контроллеров автоматизации, таких как мастер. Проект не указан для себя что он находится в системе управления версиями; поддерживает системы управления версиями, но необходимо добавить его вручную.  
  
## <a name="registering-with-a-source-control-package"></a>Регистрация пакета управления версиями  
 При добавлении файла в проект в систему управления версиями, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> , который содержит четыре непрозрачные строки, которые используются как файлы cookie, системы управления версиями. Храните эти строки в файле проекта. Эти строки должны передаваться заглушки управления источника (Visual Studio компонент, который управляет пакеты управления исходным кодом) при запуске проекта типа путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. Это в свою очередь загружает этот пакет управления соответствующий источник и перенаправляет вызов своей реализации `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)