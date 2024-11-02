---
layout: splash
title:  "GitHub AI Models"
author: Nagul Meera
author_profile: true
---

# GitHub AI Models


### Example of GitHub Model Usage


```java
package org.example;

import com.azure.ai.inference.ChatCompletionsClient;
import com.azure.ai.inference.ChatCompletionsClientBuilder;
import com.azure.ai.inference.models.ChatCompletions;
import com.azure.ai.inference.models.ChatCompletionsOptions;
import com.azure.ai.inference.models.ChatRequestMessage;
import com.azure.ai.inference.models.ChatRequestSystemMessage;
import com.azure.core.credential.AzureKeyCredential;

import java.util.Arrays;
import java.util.List;

public final class TestChatGptMini {
    public static void main(String[] args) {
        String key = "GitHubKey";
        String endpoint = "https://models.inference.ai.azure.com";
        String model = "gpt-4o-mini";

        ChatCompletionsClient client = new ChatCompletionsClientBuilder()
                .credential(new AzureKeyCredential(key))
                .endpoint(endpoint)
                .buildClient();

        List<ChatRequestMessage> chatMessages = Arrays.asList(
                new ChatRequestSystemMessage("What is java")/*,
                new ChatRequestUserMessage("Can you explain the basics of machine learning?")*/
        );

        ChatCompletionsOptions chatCompletionsOptions = new ChatCompletionsOptions(chatMessages);
        chatCompletionsOptions.setModel(model);

        ChatCompletions completions = client.complete(chatCompletionsOptions);

        System.out.printf("%s.%n", completions.getChoice().getMessage().getContent());
    }
}

```