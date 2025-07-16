user_input = input("You: ")
relevant_memories = search_memory(user_input)
context = build_context(relevant_memories, user_input)

response = openai.ChatCompletion.create(
  model="gpt-4",
  messages=[
    {"role": "system", "content": "You are a helpful assistant with long-term memory."},
    {"role": "user", "content": context}
  ]
)
