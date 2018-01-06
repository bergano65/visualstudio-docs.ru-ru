---
title: "Пошаговое руководство: Создание специализированного редактора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9e8ea75cb96b36f885a55cbf9f174394379dc05a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-custom-editor"></a>Пошаговое руководство: Создание специализированного редактора
Шаблон проекта VSPackage можно создать простой пользовательский редактор в C++.  Шаблон проекта VSPackage больше не поддерживает проекты C# или Visual Basic. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Шаблон проекта пакета Visual Studio  
 Шаблон проекта пакета Visual Studio можно найти в **новый проект** диалогового окна в папке расширения C++  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Чтобы создать пакет VSPackage с помощью шаблона пакета Visual Studio  
  
1.  Создание проекта с помощью шаблона пакета Visual Studio.  
  
2.  Выберите **специализированного редактора** и нажмите кнопку **Далее**. **Параметры редактора** -страница.  
  
3.  Введите имя редактора в **имя редактора** поле. Введите расширение файла, необходимо иметь связанное с редактором в **расширение файла** поле. Ваш редактор будет доступен для файлов с расширением. Расширение файла, зарегистрированного для Visual Studio не для Windows. Введите имя файла по умолчанию для новых документов, создаваемых с помощью редактора в **имя файла по умолчанию** поле.  
  
4.  Нажмите кнопку **Готово** , чтобы создать VSPackage в указанной папке.  
  
### <a name="to-test-your-custom-editor"></a>Чтобы проверить пользовательский редактор  
  
1.  На **файл** последовательно выберите пункты **New** и нажмите кнопку **файл**.  
  
2.  В **установленные шаблоны** области **новый файл** выберите файл шаблона, то файл типа вы только что зарегистрирован.  
  
3.  Нажмите кнопку **откройте** для просмотра и редактирования документа.  
  
     Редактор поддерживает операции вырезания и вставки, поиска и замены и открыть нагрузки.  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)