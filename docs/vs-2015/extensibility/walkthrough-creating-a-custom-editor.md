---
title: Пошаговое руководство. Создание специализированного редактора | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b1b4e59e43a4a5aeb129464a34b96ef3f665e72
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064730"
---
# <a name="walkthrough-creating-a-custom-editor"></a>Пошаговое руководство. Создание специализированного редактора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Шаблон проекта VSPackage можно создать простой пользовательский редактор в C++.  Шаблон проекта VSPackage больше не поддерживает проекты C# или Visual Basic. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Шаблон проекта пакета Visual Studio  
 Шаблон проекта пакета Visual Studio можно найти в **новый проект** диалоговое окно в папке C++ расширяемости  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Чтобы создать VSPackage с помощью шаблона пакета Visual Studio  
  
1. Создайте проект с помощью шаблона пакета Visual Studio.  
  
2. Выберите **специализированного редактора** и нажмите кнопку **Далее**. **Параметры редактора** откроется страница.  
  
3. Введите имя редактора в **имя редактора** поле. Введите расширение файла, которое вы хотите иметь связанное с редактором в **расширение файла** поле. В редакторе доступна для файлов с этим расширением. Расширение файла регистрируется для Visual Studio, не для Windows. Введите имя файла по умолчанию для новых документов, создаваемых с помощью редактора в **имя файла по умолчанию** поле.  
  
4. Нажмите кнопку **Готово** , чтобы создать VSPackage в указанной папке.  
  
### <a name="to-test-your-custom-editor"></a>Чтобы проверить пользовательский редактор  
  
1. На **файл** последовательно выберите пункты **New** и нажмите кнопку **файл**.  
  
2. В **установленные шаблоны** области **новый файл** диалоговом окне выберите файл шаблона, то файл типа вы только что зарегистрированных.  
  
3. Нажмите кнопку **откройте** для просмотра и редактирования документа.  
  
     Редактор поддерживает операции вырезания и вставки, поиска и замены и открытым и нагрузки.  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)
