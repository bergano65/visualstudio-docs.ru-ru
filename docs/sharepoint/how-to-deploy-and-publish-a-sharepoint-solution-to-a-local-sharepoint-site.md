---
title: "Как: развертывание и публикация решения SharePoint на локальном сайте SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
ms.assetid: 73f8d6a9-4c64-4bba-ae0e-9474baf8df26
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9e643eb31062bcd81302fba6e7d35cc8dfa674b6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Практическое руководство. Развертывание и публикация решения SharePoint на локальном сайте SharePoint
  Можно развернуть или публикации решений SharePoint на локальном сервере SharePoint на компьютере разработчика. Процесс развертывания копирует WSP-файл на сервер SharePoint, устанавливает решение и активация компонентов. Только процесс публикации копирует WSP-файл на сервер SharePoint и устанавливает его. Необходимо вручную активировать его, чтобы включить его в SharePoint.  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Для развертывания решения SharePoint на локальном сервере SharePoint  
  
1.  В **обозревателе решений**, выберите проект, который вы хотите развернуть.  
  
2.  В строке меню выберите **построения**, **развернуть решение**.  
  
     WSP-файл создается и устанавливается на локальном сервере SharePoint. Кроме того активируются компоненты.  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Для публикации решения SharePoint на локальном сервере SharePoint  
  
1.  В **обозревателе решений**, откройте контекстное меню для проекта SharePoint, которую требуется опубликовать, а затем выберите **публикации**.  
  
2.  В **публикации** диалогового окна выберите **опубликовать в файловой системе** переключатель.  
  
3.  В **целевое расположение** текстовом поле введите локальный путь и нажмите кнопку **публикации** кнопки.  
  
     Ход выполнения публикации отображается в Visual Studio **вывода** окна. После завершения процесса файл решения (WSP-файл) устанавливается на локальном сервере SharePoint. Тем не менее его необходимо по-прежнему активировать для использования в SharePoint. Если файл решения уже существует, ошибку и вопросом, следует ли перезаписать существующий файл. Сведения об обновлении пакета, обратитесь к разделу об обновлении удаленные пакеты в [как: развертывание, публикация и обновление решений SharePoint на удаленном сервере](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>См. также  
 [Как: развертывание, публикация и обновление решений SharePoint на удаленном сервере](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Создание пакетов решений SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Как: Настройка пакета решения SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Практическое руководство. Добавление и удаление компонентов и элементов в пакете с помощью конструктора пакетов](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  