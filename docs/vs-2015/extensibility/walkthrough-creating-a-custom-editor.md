---
title: Пошаговое руководство. Создание настраиваемого редактора | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148869"
---
# <a name="walkthrough-creating-a-custom-editor"></a>Пошаговое руководство. Создание специализированного редактора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Шаблон проекта VSPackage может создавать простой пользовательский редактор в C++.  Шаблон проекта VSPackage больше не поддерживает проекты C# и Visual Basic. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Шаблон проекта пакета Visual Studio  
 Шаблон проекта пакета Visual Studio можно найти в диалоговом окне **Новый проект** в папке расширяемость C++.  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Создание VSPackage с помощью шаблона пакета Visual Studio  
  
1. Создайте проект с помощью шаблона пакета Visual Studio.  
  
2. Выберите параметр **Пользовательский редактор** и нажмите кнопку **Далее**. Откроется страница **Параметры редактора** .  
  
3. Введите имя редактора в поле **имя редактора** . Введите расширение файла, которое необходимо связать с редактором, в поле **расширение файла** . Редактор доступен для файлов с этим расширением. Расширение файла регистрируется только для Visual Studio, а не для Windows. Введите имя файла по умолчанию для новых документов, созданных с помощью редактора, в поле **Default File Name (имя файла по умолчанию** ).  
  
4. Нажмите кнопку **Готово** , чтобы создать VSPackage в указанной папке.  
  
### <a name="to-test-your-custom-editor"></a>Тестирование пользовательского редактора  
  
1. В меню **файл** наведите указатель мыши на пункт **создать** и выберите **файл**.  
  
2. В области **Установленные шаблоны** диалогового окна **новый файл** выберите шаблон файла, а затем — только что зарегистрированный тип файла.  
  
3. Нажмите кнопку **Открыть** , чтобы просмотреть и изменить документ.  
  
     Редактор поддерживает операции копирования и вставки, поиска и замены, а также операций открытия и загрузки.  
  
## <a name="see-also"></a>См. также:  
 [VSPackages](../extensibility/internals/vspackages.md)
