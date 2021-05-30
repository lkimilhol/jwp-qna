## 1단계 요구사항

* 아래의 DDL에 맞는 엔티티를 설계한다.

```sql
create table answer
(
    id          bigint generated by default as identity,
    contents    clob,
    created_at  timestamp not null,
    deleted     boolean   not null,
    question_id bigint,
    updated_at  timestamp,
    writer_id   bigint,
    primary key (id)
)

create table delete_history
(
    id            bigint generated by default as identity,
    content_id    bigint,
    content_type  varchar(255),
    create_date   timestamp,
    deleted_by_id bigint,
    primary key (id)
)

create table question
(
    id         bigint generated by default as identity,
    contents   clob,
    created_at timestamp    not null,
    deleted    boolean      not null,
    title      varchar(100) not null,
    updated_at timestamp,
    writer_id  bigint,
    primary key (id)
)

create table user
(
    id         bigint generated by default as identity,
    created_at timestamp   not null,
    email      varchar(50),
    name       varchar(20) not null,
    password   varchar(20) not null,
    updated_at timestamp,
    user_id    varchar(20) not null,
    primary key (id)
)

alter table user
add constraint UK_a3imlf41l37utmxiquukk8ajc unique (user_id)

```

* created_at, updated_at 값을 생성 해 줄 수 있는 클래스를 생성한다.
* User, Question, Answer 순으로 엔티티를 매핑한다.
* 각각의 엔티티 매핑을 진행하며 테스트케이스를 작성한다.