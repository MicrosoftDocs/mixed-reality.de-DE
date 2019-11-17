---
title: Azure Speech Services tutorials - 3. Adding the Azure Cognitive Services speech translation component
description: In this course, you will learn how to implement Azure Speech SDK within a mixed reality application.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: dc5300b51ccb151a2e38f9d15b84a4a9031e2bb4
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143233"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. Adding the Azure Cognitive Services speech translation component

In this tutorial, you'll learn about the Azure Cognitive Services Speech Translation component of your project, as well as how to translate into three different languages.

## <a name="instructions"></a>Anweisungen

1. Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel. Search for and select Lunarcom Translation Recognizer.

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    Disable the offline mode simulator.

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    >Before moving on, ensure that the offline mode simulator is disabled (as shown in the image above) before testing the Speech-SDK translator. In order to translate, you must be connected to the internet.

2. Click the drop-down in the Lunarcom Translation Recognizer, and select the language you would like to translate to.

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. Run the application and test the translator by clicking the Satellite button, and begin speaking. Press the Satellite button again to stop the recognition. Below is an example of what your scene should look like. Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.

    Below is an example of what your scene should look like:

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Your project can now successfully translate the words you speak into several different languages. Feel free to play around with the languages, and test the accuracy of the translation.

[Nächstes Tutorial: 4. Einrichten der Absicht und der Kenntnisse in natürlicher Sprache](mrlearning-speechSDK-ch4.md)
