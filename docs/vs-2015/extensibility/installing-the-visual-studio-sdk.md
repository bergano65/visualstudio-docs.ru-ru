---
title: Установка пакета SDK для Visual Studio | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88a6266a3f5910def0bf5041a37f89c2b3d67416
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843427"
---
# <a name="installing-the-visual-studio-sdk"></a>Установка пакета SDK для Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Установка пакета SDK для Visual Studio в составе установки Visual Studio  
 Если вы хотите включить VSSDK в установку Visual Studio, необходимо выполнить выборочную установку.  
  
> [!NOTE]
> В исполняемом файле установки пакет SDK для Visual Studio называется **средства расширения Visual Studio**.  
  
1. Запустите установку Visual Studio 2015. Можно установить любой выпуск Visual Studio, кроме Express.  
  
2. На первом экране выберите **Пользовательский**, а не **используемый по умолчанию**. Нажмите кнопку **Далее**.  
  
3. Вы должны увидеть представление пользовательских функций в виде дерева. Откройте **Общие инструменты**. Вы должны увидеть **средства расширения Visual Studio** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4. Установите флажок **средства расширения Visual Studio** , а затем нажмите кнопку **Далее** и продолжите установку.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Установка пакета SDK для Visual Studio после установки Visual Studio  
 Если вы решили установить пакет SDK для Visual Studio после завершения установки Visual Studio, выполните следующую процедуру:  
  
1. Перейдите в раздел **Панель управления/программы/программы и компоненты**и найдите **Visual Studio 2015**. Пакет SDK для Visual Studio можно установить для любого выпуска Visual Studio 2015, кроме Express.  
  
2. Щелкните правой кнопкой мыши **Visual Studio 2015**и выберите пункт **изменить**. Должна отобразиться страница установки.  
  
3. Выполните ту же процедуру, что и в разделе **Установка пакета SDK для Visual Studio как часть установки Visual Studio** выше.  
  
4. Щелкните ссылку **средства расширения Visual Studio** , чтобы установить пакет SDK для Visual Studio.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Установка пакета SDK для Visual Studio из решения  
 Если вы откроете решение с проектом расширения среды без предварительной установки VSSDK, появится запрос на выделенную информационную панель над обозреватель решений. Это выглядит примерно так:  
  
 ![солутионексплореринсталл](../extensibility/media/solutionexplorerinstall.png "солутионексплореринсталл")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Установка пакета SDK для Visual Studio из командной строки  
 Вы можете установить VSSDK из командной строки с помощью параметра **/инсталлселектаблеитемс** с установщиком Visual Studio. Дополнительные сведения об использовании параметров командной строки с установщиком см. в разделе [Installing Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 Вот как можно установить VSSDK автоматически с помощью установщика сообщества Visual Studio 2015:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Обратите внимание на то, что вам необходимо использовать установщик Visual Studio, соответствующий установленной версии Visual Studio. Например, если на компьютере установлен Visual Studio Enterprise, необходимо запустить установщик Visual Studio Enterprise (vs_enterprise. exe).
