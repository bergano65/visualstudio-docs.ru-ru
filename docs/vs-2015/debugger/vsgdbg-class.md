---
title: Класс VsgDbg | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 053647d48324f056148375bae9268b997ba8721f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145696"
---
# <a name="vsgdbg-class"></a>Класс VsgDbg
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Представляет интерфейс для управления программными компонент диагностики графики в приложении.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
class VsgDbg;  
```  
  
## <a name="members"></a>Участники  
 `VsgDbg` Класс поддерживает следующие члены.  
  
### <a name="public-constructors"></a>Открытые конструкторы  
  
|name|Описание|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (конструктор)](../debugger/vsgdbg-vsgdbg-constructor.md)|Создает экземпляр класса `VsgDbg` класса и при необходимости подготавливает компонент диагностики графики для активного захвата и записи данных графики в приложении.|  
|[VsgDbg::~VsgDbg (деструктор)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Уничтожает экземпляр `VsgDbg` класса.|  
  
### <a name="public-methods"></a>Открытые методы  
  
|name|Описание|  
|----------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|Добавляет пользовательское сообщение на головной дисплей (HUD) диагностики графики.|  
|[BeginCapture](../debugger/begincapture.md)|Начинается интервал захвата, будут заканчиваться `EndCapture`.|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Захватывает оставшуюся часть текущего кадра в файл журнала графики.|  
|[Copy (программный захват)](../debugger/copy-programmatic-capture.md)|Копирует содержимое активного файла журнала графики (.vsglog) в новый файл.|  
|[EndCapture](../debugger/endcapture.md)|Завершает интервал захвата, начатый функцией `BeginCapture`.|  
|[Init](../debugger/init.md)|Подготавливает компонент диагностики графики для активного захвата и записи данных графики в приложении.|  
|[ToggleHUD](../debugger/togglehud.md)|Переключает наложение HUD диагностики графики, включить или отключить.|  
|[UnInit](../debugger/uninit.md)|Финализирует файл журнала графики, закрывает его и освобождает все ресурсы, которые использовались во время активной записи данных графики приложением.|  
  
## <a name="remarks"></a>Примечания  
 `VsgDbg` Класс представляет интерфейс, который можно использовать для управления функциями диагностики графики программными средствами. Можно использовать некоторые возможности, даже в том случае, если вы не активно захвата и записи данных графики; Сюда входят `AddMessage` функция-член и `ToggleHUD` функция-член. Другие функции-члены Подготовка компонент в приложении диагностики графики для запуска или остановки active захвата графических данных либо должен вызываться, пока приложение активно захват и запись сведений графики файла журнала графики.
