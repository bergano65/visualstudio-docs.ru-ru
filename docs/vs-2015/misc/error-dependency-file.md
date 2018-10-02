---
title: 'Ошибка: зависимость &#39;файл&#39; в проекте &#39;проекта&#39; не может быть скопирован в каталог выполнения из-за конфликта с зависимостью &#39;файл&#39; | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: douge
ms.openlocfilehash: 6f571ec21094a28077f63bf86d4afe97af5429dd
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2018
ms.locfileid: "47592516"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>Ошибка: зависимость &#39;файл&#39; в проекте &#39;проекта&#39; не может быть скопирован в каталог выполнения из-за конфликта с зависимостью &#39;файла&#39;
Существует конфликт между ссылками. Чтобы запустить приложение, необходимо скопировать несколько разных файлов сборки с одинаковым именем файла в каталог bin. Каталог запуска не может разрешить конфликт, так как ни одна из зависимостей не является первичной ссылкой.  
  
 Эта ошибка приведет к сбою процесса сборки.  
  
 Дважды щелкните элемент списка задач, чтобы перейти к узлу ссылок проекта, в котором произошел конфликт.  
  
 **Чтобы исправить эту ошибку**  
  
-   Сделайте одну из сборок прямой ссылкой проекта. Возможным недостатком этого подхода является то, что выбранная сборка может не работать со сборками, которым требуется другая версия указанной по ссылке сборки.  
  
     \- или -  
  
-   Убедитесь, что обе копии сборки имеют строгие имена и находятся в глобальном кэше сборок. Это исключает необходимость копировать сборки в папку bin.  
  
## <a name="see-also"></a>См. также  
 [Управление ссылками в проекте](../ide/managing-references-in-a-project.md)   
 [Глобальный кэш сборок](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [Сборки со строгими именами](http://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Управление версиями сборок](http://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903)   
 [Практическое руководство. Создание и удаление зависимостей проекта](../ide/how-to-create-and-remove-project-dependencies.md)