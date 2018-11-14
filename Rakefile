# Add your own tasks in files placed in lib/tasks ending in .rake,
# for example lib/tasks/capistrano.rake, and they will automatically be available to Rake.

require_relative 'config/application'

namespace :rabbitmq do
  desc "Setup routing"
  task :setup do
    require "bunny"

    conn = Bunny.new
    conn.start

    ch = conn.create_channel

    # connect one exchange to multiple queues
    x = ch.fanout("blog.posts")
    ch.queue("dashboard.posts", durable: true).bind("blog.posts")
    ch.queue("admin.posts", durable: true).bind("blog.posts")

    # connect mutliple exchanges to the same queue
    x = ch.fanout("admin.page_views")
    ch.queue("dashboard.page_views", durable: true).bind("admin.page_views")

    x = ch.fanout("blog.page_views")
    ch.queue("dashboard.page_views", durable: true).bind("blog.page_views")

    conn.close
  end
end

Rails.application.load_tasks
