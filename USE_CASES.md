# Use cases

## Consumer API and Producer API

The **topic naming convention** has been set to: `message_type.application_name.entity_name` (all in snake_case, it can be changed of course):

- message_type: queuing, logging, tracking, etl/db, streaming, push, user...
- application_name: the application base name
- entity_name: the entity name (or the prefix if no entity) which is consumed

### Define your configuration Step-by-step

This module allows the user to write new Kafka configuration (new Java files and `application.yml` updates). In order to achieve it, prompt options are asked step-by-step until you decide to finish your configuration.

You can choose to merge the new configuration with the previous configuration or just replace it, by typing `y` or `n` to the question "Do you want to clean up your current Kafka configuration?".

### Create a consumer linked to an entity

After following the first 3 steps of the [basic usage](README.md#basic-usage) above, choose a mode and follow the steps:

1. Create a new entity if not already generated with: `jhipster entity Foo`
2. In the same folder, run `yo jhipster-kafka`
3. "Do you want to clean up your current Kafka configuration?" - Your answer or 'n' by default
4. "What is your bootstrap servers string connection (you can add several bootstrap servers by using a "," delimiter)?" - Your answer or 'localhost:9092' by default
5. "For which entity (class name)?" - Foo (the available entities are retrieved in the `.jhipster` folder as `.json`)
6. "Which components would you like to generate?" - Consumer
7. "Which topic for Foo?" - Any choice (choosing "Custom topic name" will add another question "What is the topic name for Foo?")
8. "What is the consumer polling timeout (in ms)?" - Your answer or '10000' by default (global for all consumers)
9. "Define the auto offset reset policy?" - Your answer or 'earliest' by default (global for all consumers)
10. "Do you want to continue adding consumers or producers?" - Your answer or 'N' par default
11. Overwrite all files in conflict
12. `FooConsumer` (consumes `Foo`) is available with a `FooDeserializer`

### Create a producer linked to an entity

After following the first 3 steps of the [basic usage](README.md#basic-usage) above, choose a mode and follow the steps:

1. Create a new entity if not already generated with: `jhipster entity Foo`
2. In the same folder, run `yo jhipster-kafka`
3. "Do you want to clean up your current Kafka configuration?" - Your answer or 'n' by default
4. "What is your bootstrap servers string connection (you can add several bootstrap servers by using a "," delimiter)?" - Your answer or 'localhost:9092' by default
5. "For which entity (class name)?" - Foo (the available entities are retrieved in the `.jhipster` folder as `.json`)
6. "Which components would you like to generate?" - Producer
7. "Which topic for Foo?" - Any choice (choosing "Custom topic name" will add another question "What is the topic name for Foo?")
8. "Do you want to send ordered messages for (entity/prefix) production?" - Your answer or 'y' by default
9. "Do you want to continue adding consumers or producers?" - Your answer or 'N' par default
10. Overwrite all files in conflict
11. `FooProducer` (produces `Foo`) is available with a `FooSerializer` and a `FooKafkaResource` to [help testing](README.md#test-consumers-and-producers)

### Create a consumer NOT linked to an entity

After following the first 3 steps of the [basic usage](README.md#basic-usage) above, choose a mode and follow the steps:

1. Create a new entity if not already generated with: `jhipster entity Foo`
2. In the same folder, run `yo jhipster-kafka`
3. "Do you want to clean up your current Kafka configuration?" - Your answer or 'n' by default
4. "What is your bootstrap servers string connection (you can add several bootstrap servers by using a "," delimiter)?" - Your answer or 'localhost:9092' by default
5. "For which entity (class name)?" - No entity (will be typed String)
6. "How would you prefix your objects (no entity, for instance: [SomeEventType]Consumer|Producer...)?" - someEventType
7. "Which components would you like to generate?" - Consumer
8. "Which topic for someEventType?" - Any choice (choosing "Custom topic name" will add another question "What is the topic name for someEventType?")
9. "What is the consumer polling timeout (in ms)?" - Your answer or '10000' by default (global for all consumers)
10. "Define the auto offset reset policy?" - Your answer or 'earliest' by default (global for all consumers)
11. "Do you want to continue adding consumers or producers?" - Your answer or 'N' par default
12. Overwrite all files in conflict
13. `SomeEventTypeConsumer` (consumes `String`) is available with a `SomeEventTypeDeserializer`

### Create a producer NOT linked to an entity

After following the first 3 steps of the [basic usage](README.md#basic-usage) above, choose a mode and follow the steps:

1. Create a new entity if not already generated with: `jhipster entity Foo`
2. In the same folder, run `yo jhipster-kafka`
3. "Do you want to clean up your current Kafka configuration?" - Your answer or 'n' by default
4. "What is your bootstrap servers string connection (you can add several bootstrap servers by using a "," delimiter)?" - Your answer or 'localhost:9092' by default
5. "For which entity (class name)?" - No entity (will be typed String)
6. "How would you prefix your objects (no entity, for instance: [SomeEventType]Consumer|Producer...)?" - someEventType
7. "Which components would you like to generate?" - Producer
8. "Which topic for someEventType?" - Any choice (choosing "Custom topic name" will add another question "What is the topic name for someEventType?")
9. "Do you want to send ordered messages for (entity/prefix) production?" - Your answer or 'y' by default
10. "Do you want to continue adding consumers or producers?" - Your answer or 'N' par default
11. Overwrite all files in conflict
12. `SomeEventTypeProducer` (produces `String`) is available with a `SomeEventTypeSerializer` and a `SomeEventTypeKafkaResource` to [help testing](README.md#test-consumers-and-producers)
